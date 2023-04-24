---
layout: post
title: "Learning GNU C __attribute__"
date: 2023-04-22
---

## What is `__attribute__`?


The `__attribute__` mechanism can decorate variables, assign characteristic to declared functions, and etc. It is a mechanism to allow programmers interact with compilers. Programmiers can utilize attribute mechanism to explicitly tell compilers some behaviros are intentional, such as
 * Do not report them as neither warnings, erros, or undefined behavirors. 
 * Do not optimize them. 
 * ...

I believe if Rust language has this mechanism, some programmers would like tell Rust compilers:

> **Do NOT panic on my code !!!**.


The following content are based on that essay: [Using GNU C \_\_attribute\_\_](http://unixwiz.net/techtips/gnu-c-attributes.html)

### \_\_attribute\_\_ unused

It is not always possible to remove ununsed variables or parameters.

```C
/* test.c */

/* 
 * $ gcc -Wall -Wextra test.c
 * test.c: In function ‘main’:
 * test.c:8:14: warning: unused parameter ‘argc’ [-Wunused-parameter]
 *     8 | int main(int argc, char **argv) {
 *       |          ~~~~^~~~ 
 */
#include <stdio.h>

int main(int argc, char **argv) {
    /* code that uses argv, but not argc */
    char *program_name = argv[0];
    printf("program name is %s\n", program_name);
    return 0;
}
```
The warning can be eliminated with `__attribute__ unused`

```C
#include <stdio.h>

int main( int argc __attribute__((unused)), char **argv) {
    /* code that uses argv, but not argc */
    char *program_name = argv[0];
    printf("program name is %s\n", program_name);
    return 0;
}
```

According to the doc [Options to Request or Suppress Warnings](https://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html#index-W), the compile option `-Wall` and `-Wextra` are both required to produce the warning.

The `-Wextra` option enables the `-Wunused-parameter (only with -Wunused or -Wall)` warnings flags. We can use `-Wunused-parameter` instead.

The position of `__attribute__` matters. In the above example, we can either put the `__attribute__ ((unused))` before or after the parameter. However, it might be different if we want to add attribute to variables [^va] or functions [^fa] [^cfa].

[^va]: [Variable attributes](https://www.ibm.com/docs/en/i/7.1?topic=declarators-variable-attributes)
[^fa]: [Function attributes](https://gcc.gnu.org/onlinedocs/gcc/Attribute-Syntax.html#Attribute-Syntax)
[^cfa]: [Common Function Attributes](https://gcc.gnu.org/onlinedocs/gcc/Common-Function-Attributes.html#Common-Function-Attributes)



The combination of `DEBUG` macro and `unused` attribute:

```C
/* mypid.c */

/*
 * $ gcc -Wall -Wextra mypid.c -o mypid -DDEBUG
 * $ ./mypid
 * program name is ./mypid
 * My PID = 236429
 */

#include <stdio.h>
#include <unistd.h>

/* warning: 'someFunction' declared 'static' but never defined */
static int someFunction() __attribute__((unused));

int main(int argc __attribute__((unused)), char **argv)
{
	/* code that uses argv, but not argc */
	char *program_name = argv[0];
	printf("program name is %s\n", program_name);

	/* warning: unused variable 'mypid' */
	int mypid __attribute__((unused)) = getpid();

#ifdef DEBUG
	printf("My PID = %d\n", mypid);
#endif

	return 0;
}
```

The program only uses the variable `mypid` when `DEBUG` option is enabled. If the developer did not enable the `DEBUG` option, the `__attribute__ ((unused))` suppressed the warning.









