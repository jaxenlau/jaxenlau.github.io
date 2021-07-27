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
如果没有安装 brew 可以安装 brew，如果已经安装，忽略此步骤
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

安装 gsed，因为 mac 自带 sed 与 gnu sed 有所区别，所以为了方便这里只介绍 gsed
```bash
brew install gnu-sed
```

``` bash
gsed "s/\/\/\s*/\/\/ /g" -i $FilePath$
```

## Linux
```bash
sed "s/\/\/\s*/\/\/ /g" -i $FilePath$
```