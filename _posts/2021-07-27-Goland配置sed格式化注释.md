---
layout: post
title: "Goland配置sed格式化注释"
date: 2021-07-27 16:20:36 +0800
categories: Golang
tags: [function, golang]
typora-root-url: ../../jaxenlau.github.io
typora-copy-images-to: ../images
---

## Mac
``` bash
gsed "s/\/\/\s*/\/\/ /g" -i $FilePath$
```

如果没有安装 brew 可以安装 brew，如果已经安装，忽略此步骤
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

如果没有安装 gnu-sed，使用 brew 安装 gnu-sed，因为 mac 自带 sed 与 gnu sed 有所区别，所以为了方便这里只介绍 gnu-sed
```bash
brew install gnu-sed
```

## Linux
```bash
sed "s/\/\/\s*/\/\/ /g" -i $FilePath$
```

## 配置 Goland

1. 路径 `Preferences...` -> `Tool` ->  `File Watchers` -> `<custom>`
2. Name : `gsed comment`
3. File Type: `Go`
4. Scope: `Project Files`
5. Program:  `gsed`
6. Arguments:  `"s/\/\/\s*/\/\/ /g" -i $FilePath$`
7. Advanced Options 中的所有选项都取消选定，不然会出现一直触发的问题

