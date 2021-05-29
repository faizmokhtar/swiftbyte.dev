---
layout: post
title: How to supercharge your Xcode debugging experience with Chisel
date: 2021-05-17T12:40:43.470Z
categories:
  - tips
  - tools
---
[Chisel][1] is a collections of LLDB commands develop by Facebook to help debug our iOS apps.

# How to install

```bash
brew update && brew install chisel
```
Then, we have to create and update our `.lldbinit` file in the root folder.
```bash
cd ~
touch .lldbinit
open .lldbinit
```
Append the following line to your `.lldbinit` file. This will make sure that Chisel is imported whenever we launch Xcode.
```bash
command script import /usr/local/opt/chisel/libexec/fbchisellldb.py
```

[1]: https://github.com/facebook/chisel