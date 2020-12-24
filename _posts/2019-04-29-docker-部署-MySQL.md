---
layout: post
title: docker 部署 MySQL
date: 2019-04-29 12:17:10 +0800
categories: MySQL
tags: [docker, mysql]
typora-root-url: ../../jaxenlau.github.io
typora-copy-images-to: ../images
---

Docker 一键部署 MySQL 笔记备忘

### 安装 mysql-client：

- MAC：`brew install mysql-client`
- CentOS：`yum install mysql`

### 安装 mycli 

可替代 mysql-client，支持语法高亮和语法自动补全提示：

- GitHub: <https://github.com/dbcli/mycli>
- MAC：`brew install mycli`
- CentOS: `pip3 install -U mycli` (需要依赖 python 环境)

### Docker 启动 MySQL

#### 原生方式

```shell
docker pull mysql:5.7

cd /Users/owenliu/lehui/data/docker_mysql_data

docker run -p 3306:3306 --name mymysql -v $PWD/conf:/etc/mysql/conf.d -v $PWD/logs:/logs -v $PWD/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7
```

#### docker-compose

docker-compose.yaml

``` yaml
version: "3"

services:
  mysql57: 
    container_name: mymysql
    image: mysql:5.7
    ports: 
      - 3306:3306
    environment:
      MYSQL_ROOT_PASSWORD: 123456
    volumes: 
      - ./conf::/etc/mysql/conf.d
      - ./data:/var/lib/mysql
      - ./logs:/logs
```



