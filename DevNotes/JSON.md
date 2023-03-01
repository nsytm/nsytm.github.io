---
layout: default
title: JSON
parent: DevNotes
nav_order: 2
---

# JSON
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


### 1、Jackson

SpringBoot默认的json解析框架就是Jackson，所以不需要额外的引入依赖。

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

记录一下工作中常用的注解:

- @JsonProperty

  注解一般用于实体类的属性上，作用是在序列化时给该属性重命名。序列化和反序列化都受影响。

  在和第三方系统对接时，可能对方提供的接口文档中，有字段不符合Java变量命名规范，如”APPID“，我们命名的是”appId“，这样的话我们调对方接口就会报错。

```java
@Data
@Accessors(chain = true)
public class DemoVO implements Serializable {
    
    private static final long serialVersionUID = 1L;

    /**
     * 来源appId
     */
    @JsonProperty("APPID")
    private String appId;
    
}
```

- @JsonIgnoreProperties

  注解用在实体类上，用于忽略实体类中不存在的属性，也可以指定要忽略的属性。序列化和反序列化都受影响。

  在和第三方系统对接中，我们根据对方提供的接口文档编写实体类，但实际接口调用中，可能会出现文档中未定义的字段，当请求返回时就会报错。

```java
@Data
@Accessors(chain = true)
@JsonIgnoreProperties(ignoreUnknown = true) // 忽略不存在的字段
@JsonIgnoreProperties(value = {"appId", "appKey"}) // 指定的的字段不会被序列化和反序列化
public class DemoVO implements Serializable {

    private static final long serialVersionUID = 1L;

    /**
     * 交易号（报文唯一标识码）
     */
    private String transCode;

    /**
     * 来源appId
     */
    private String appId;

    /**
     * 来源appKey
     */
    private String appKey;

}
```
