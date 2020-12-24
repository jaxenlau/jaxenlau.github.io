---
layout: post
title: docker 部署 Redis
date: 2019-04-29 12:15:11 +0800
categories: Redis
tags: [docker, redis]
typora-root-url: ../../jaxenlau.github.io
typora-copy-images-to: ../images
description: docker 一键部署本地 Redis 测试环境
---

## 原生方式启动

``` shell
docker pull  redis

cd /Users/owenliu/lehui/data/redis_data

docker run -p 6379:6379 -v $PWD:/data  -d redis redis-server --appendonly yes

src/redis-cli -h localhost -p 6379
```



## docker-compose 方式启动

docker-compose.yaml

``` yaml
version: "3"

services:
  redis: 
    command: redis-server /usr/local/etc/redis/redis.conf 
    container_name: redis_server
    image: redis
    ports: 
      - 6379:6379
    volumes: 
      - ./redis.conf:/usr/local/etc/redis/redis.conf
      - ./data:/data
```

redis.conf

``` ini
requirepass 123456
appendonly yes
daemonize no
```

``` bash
docker-compose up -d
```

