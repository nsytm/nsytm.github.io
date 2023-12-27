---
layout: default
title: JSON
parent: DevNotes
nav_order: 0
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


#### 1.1、@JsonProperty

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

#### 1.2、@JsonIgnoreProperties

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

#### 1.3、@JsonSerialize(using = ToStringSerializer.class)

注解用于实体类的属性上，将对象的某个属性转换成字符串。解决Jackson序列化时Long类型精度缺失问题。

```java
import com.fasterxml.jackson.databind.annotation.JsonSerialize;
import com.fasterxml.jackson.databind.ser.std.ToStringSerializer;

public class Person {

    @JsonSerialize(using = ToStringSerializer.class)
    private Long id;

}
```

#### 1.4、LocalDateTime序列化和反序列化失败

[参考文档：](https://blog.csdn.net/qq991658923/article/details/121873279)

```java
public class Person {

    @JsonSerialize(using = LocalDateTimeSerializer.class)
    @JsonDeserialize(using = LocalDatetimeDeserializer.class)
    private LocalDateTime time;

}
```
