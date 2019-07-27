title: MyBatis传入参数
author: Sion
tags:
  - MyBatis
categories: []
date: 2019-07-27 14:41:00
---
#### 传入参数不只一个
可以不使用`parameterType`同时在对应接口的参数中加上`@Param("")`即可

例子：

```java
public AddrInfo getAddrInfo(@Param("corpId")int corpId, @Param("addrId")int addrId);
```
<!-- more -->

xml配置这样写：

```xml
<select id="getAddrInfo"  resultMap="com.xxx.xxx.AddrInfo">
       SELECT * FROM addr__info 
　　　　where addr_id=#{addrId} and corp_id=#{corpId}
</select>
```