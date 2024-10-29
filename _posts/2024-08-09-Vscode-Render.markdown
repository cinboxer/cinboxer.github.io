---
layout:     post
title:      "VScode markdown render渲染器出错"
subtitle:   " \"VScode markdown render渲染器出错\""
date:       2024-08-09 20:00:00
author:     "Mickle"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - Debug
---

更新VScode后出现了这个错误：

VSCODE no renderer found for ‘text/markdown’

找到原因可能是扩展页面的`@builtin markdown` 的扩展内置插件被禁止了

Enable后重启就好了

