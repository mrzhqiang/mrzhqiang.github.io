---
layout: post
title: Spring Boot | 配置文件
---

# Spring Boot 配置文件
配置文件

## 一、生效顺序
配置文件的生效顺序：
1. 启动时的命令行
2. 来自 java:comp/env 的 JNDI 属性
3. Java 系统属性/系统环境变量
4. RandomValuePropertySource 配置的 random.* 属性值
5. file:./application-{profile}.yaml
6. file:./application.yaml
7. classpath:config/application-{profile}.yaml
8. classpath:config/application.yaml
9. classpath:application-{profile}.yaml
10. classpath:application.yaml
11. @Configuration 注解类上的 @PropertySource 指定的文件
12. 通过 SpringApplication.setDefaultProperties 指定的默认属性