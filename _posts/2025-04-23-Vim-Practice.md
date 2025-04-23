---
layout: post
title: "Vim Practice"
date: 2025-04-23
---

## Vim macro to create a numbered list

I was reading a book and wanted to take some notes. Now I need to creat a list like follows:

```
##### 1.1.1
##### 1.1.2
##### 1.1.3
##### 1.1.4
##### 1.1.5
##### 1.1.6
##### 1.1.7
##### 1.1.8
##### 1.1.9
##### 1.1.10
##### 1.1.11
##### 1.1.12
##### 1.1.13
##### 1.1.14
##### 1.1.15
##### 1.1.16
##### 1.1.17
##### 1.1.18
##### 1.1.19
##### 1.1.20
##### 1.1.21
##### 1.1.22
##### 1.1.23
##### 1.1.24
##### 1.1.25
##### 1.1.26
##### 1.1.27
##### 1.1.28
##### 1.1.29
##### 1.1.30
##### 1.1.31
##### 1.1.32
##### 1.1.33
##### 1.1.34
##### 1.1.35
##### 1.1.36
```

I asked both ChatGPT and Gemini. They both give the answer to write a for loop in the first prompt. After I told them that I already have the first line `##### 1.1.1` and I want to do copy and past, increase the last number, so on so forth, ChatGPT undertood what I was trying to do, and then generated the guidance:

🎯 Goal:
Start with one line:

```vim
##### 1.1.1
```

🪄 Step-by-step:
1. Place your cursor on the line `##### 1.1.1`

2. Press `qq` to start recording a macro into register `q`

3. Press the following key sequence carefully:

```vim
Y               " Yank the current line
p               " Paste it below
Ctrl-a          " Increment the last number (assumes cursor lands on the number)
```

4. Press `q`  again to stop recording

▶️ Run the macro 35 more times:
```vim
35@q
```
