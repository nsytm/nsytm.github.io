---
layout: default
title: JAXB
parent: DevNotes
nav_order: 0
---

# JAXB
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


### 1、JAXB 简介

JAXB（Java Architecture for XML Binding）是Java的一个API，它允许将XML文档与Java对象之间相互转换。它是Java SE
6及以上版本中自带的一部分，因此可以通过JDK自带的库使用。JAXB通过自动生成Java类来绑定XML文档和Java对象之间的关系。这些Java类使用注解来标识与XML元素和属性之间的映射关系。通过将XML文档解组成Java对象，以及将Java对象序列化为XML文档，可以轻松地在Java应用程序中处理XML数据。

#### 1.1、JAXB 核心接口

1. JAXBContext

   JAXBContext是JAXB的核心接口之一，它提供了将Java对象和XML文档之间进行转换所需的所有信息。JAXBContext实例通常用于创建Marshaller和Unmarshaller对象，用于将Java对象转换为XML文档和将XML文档转换为Java对象。

2. Marshaller

   Marshaller是JAXB用于将Java对象序列化为XML文档的核心接口。Marshaller对象可以使用JAXBContext创建，通过调用marshal()
   方法将Java对象转换为XML文档。Marshaller可以控制生成的XML文档的格式，包括指定XML文档的编码格式、缩进、换行等。

3. Unmarshaller

   Unmarshaller是JAXB用于将XML文档反序列化为Java对象的核心接口。Unmarshaller对象可以使用JAXBContext创建，通过调用unmarshal()
   方法将XML文档转换为Java对象。Unmarshaller可以自动识别XML文档的根元素并创建对应的Java对象。

4. XmlRootElement

   XmlRootElement是JAXB用于指定Java对象映射为XML文档时的根元素名称的注解。XmlRootElement注解需要应用在Java类上，指定类映射为XML文档的根元素名称和命名空间。

5. XmlElement

   XmlElement是JAXB用于指定Java对象属性和XML元素之间的映射关系的注解。XmlElement注解需要应用在Java属性上，指定属性映射为XML元素名称和命名空间。除此之外，XmlElement还可以用于指定Java属性的默认值、是否必须等信息。

#### 1.2、JAXB 注解

1. #### @XmlRootElement

   指定一个类或枚举类型作为XML文档的根元素的注解。

   ```java
   @XmlRootElement(name = "ROOT")
   public class Root {
   	...
   }
   ```


2. #### @XmlElement

   指定Java类的一个字段或方法映射到XML文档中的一个元素。

   ```java
   public class SecurityInfo {
       @XmlElement(name = "SYSTEM_ID")
       private String systemId;
   }
   ```


3. #### @XmlAttribute

   指定Java类的一个字段映射为XML元素的属性。

   ```java
   public class BaseData {
       @XmlAttribute(name = "USER_NAME")
       private String userName;
   }
   ```

4. #### @XmlAccessorType

   指定JAXB序列化和反序列化时访问类的属性或字段的方式。它决定了哪些成员会被包含在XML中，以及如何访问和处理它们。参数value
   可以接受4个指定值：

   XmlAccessType.FIELD：映射类中非静态、非瞬态的字段（成员变量）到XML

   XmlAccessType.PROPERTY：映射类中的属性（get/set方法）到XML

   XmlAccessType.PUBLIC_MEMBER：映射类中所有public修饰的属性和字段到XML（默认）

   XmlAccessType.NONE：忽略所有字段

   注意点：不参与 JAXB 序列化和反序列化的一些情况

   ```java
   @XmlAccessorType(XmlAccessType.FIELD)
   public class Root {
       // 瞬态字段不参与 JAXB 的序列化和反序列化
       private transient String transientString;
       // 静态字段不参与 JAXB 的序列化和反序列化
       private static String staticString;
       // @XmlTransient 注解不参与 JAXB 的序列化和反序列化
       @XmlTransient
       private String systemId;
   }
   ```

5. #### @XmlElementWrapper

   指定包装集合或数组元素的XML元素的名称。一般配合@XmlElement注解使用。

   ```java
   public class MyClass {
       @XmlElementWrapper(name = "SYSTEM_IDS")
       @XmlElement(name = "SYSTEM_ID")
       private List<String> systemIds;
   }
   ```

   ```xml
   <MyClass>
       <SYSTEM_IDS>
           <SYSTEM_ID>Q159</SYSTEM_ID>
           <SYSTEM_ID>W160</SYSTEM_ID>
       </SYSTEM_IDS>
   </MyClass>
   ```


6. #### @XmlTransient

   将某个属性或字段标记为不参与XML序列化和反序列化过程，即忽略该属性或字段的处理。

   ```java
   public class MyClass {
       @XmlTransient
       private String systemId;
   }
   ```

7. 55

### 2、JAXB 参考文档

- [Java 8 版本的官方文档](https://docs.oracle.com/javase/8/docs/api/)
- [@XmlAccessorType](https://docs.oracle.com/javase/8/docs/api/javax/xml/bind/annotation/XmlTransient.html)
- [博客文档](https://www.cnblogs.com/wuyongyin/p/14317489.html)

### 3、JAXB 使用

如果你可以在报文中直接拿到XML String，那么可以直接使用Apache Commons Lang库中的StringEscapeUtils.unescapeXml()
方法将实体引用转换回原字符。以下是一个示例代码：

// 假设xmlString是从HTTP POST请求中获取的XML报文字符串
String xmlString = "<root>&lt;child&gt;value&lt;/child&gt;</root>";
// 将实体引用转换回原字符
xmlString = StringEscapeUtils.unescapeXml(xmlString);
// 输出转换后的XML报文
System.out.println(xmlString);

JaveSE

https://blog.csdn.net/cyan20115/article/details/106540963

https://blog.csdn.net/qq_45167987/article/details/124948631























