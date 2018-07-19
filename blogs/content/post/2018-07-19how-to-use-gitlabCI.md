---
layout:     post
title:      "gitlab-ci-cd搭建持续集成环境"
subtitle:   ""
description: "GitLab Continuous Integration & Deployment"
date:       2018-07-19 11:00:00
author:     "杨志强"
image:      "img/post-bg-baihaba.jpg"
published: true
tags:
    - tech
    - devOps
URL: "/2018/07/19/how-to-use-gitlabCI/"
categories: [ tech ]
---

# gitlab配置Devops
### runner配置
- executo默认使用shell本地构建,[runner详细配置](https://gitlab.com/gitlab-org/gitlab-runner/blob/master/docs/configuration/advanced-configuration.md "runner配置")
- runner执行过程中遇到docker权限问题，runner以--user gitlab-runner启动，将此用户加入docker用户组即可
```
vi /etc/passwd
用户名:口令:用户标识号:组标识号:注释性描述:主目录:登录Shell
```

### .gitlab-ci.yml
- [在线语法测试](http://192.168.251.157/root/spring-boot-docker/-/ci/lint)
- 基础使用

```
build:
  stage: build
  script:
    - mvn compile
  tags:
    - tag-157
```
- [使用gitlab ci部署springboot应用到k8s](https://about.gitlab.com/2016/12/14/continuous-delivery-of-a-spring-boot-application-with-gitlab-ci-and-kubernetes/ "使用gitlab ci部署springboot应用到k8s")
