---
layout:     post
title:      "Failure to start kernel due to failures in importing modules from files"
subtitle:   " \"VScode 无法 start kernel\""
date:       2025-01-27 00:20:00
author:     "Mickle"
header-img: "img/new/boston.jpg"
catalog: true
tags:
    - python
    - code
    - Debug
---

# Content
- Website: https://github.com/microsoft/vscode-jupyter/wiki/Failure-to-start-kernel-due-to-failures-in-importing-modules-from-files

- Sometimes, the inability of a kernel to start can be traced back to conflicts caused by user-defined code files named after standard Python libraries, such as `os.py`, `random.py`, or even `code.py`. When Python encounters a file with the same name as a built-in module, it prioritizes the user-defined file over the standard library during the import process. This can lead to unexpected behavior, as the interpreter attempts to execute your file in place of the intended system module, causing errors or even preventing the kernel from initializing properly. To avoid such conflicts, ensure that your custom files are named uniquely and avoid reusing names of built-in Python modules. Additionally, checking your working directory for conflicting files and cleaning up your namespace can save time and frustration when troubleshooting kernel issues.

