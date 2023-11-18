---
UID: 20230423101259 
title: "{{title}}"
tags: 
aliases: 
source: 
cssclass: 
created: 2023-04-23
Update: NaN
---

## ✍内容
上午：
数据库接口编写
连接数据库遇见问题连接超时，检查多次代码，数据库无果，
通过查找资料发现，报错原因是 nodejs 在后台使用 ipv6，所以 localhost 不是指向 127.0.0.1，
Const timeoutError = new error_1.MongoServerSelectionError(`Server selection timed out after ${serverSelectionTimeoutMS} ms`, this.description);
解决方案：将 localhost 手动改为 127.0.0.1
下午：
1. 编写前端 demo，使用 node 写 mongodb 接口进行测试
遇到问题：在添加数据是，返回妆台为 200 成功但是数据没有写入到数据库，
解决方案：因为使用 postcode 进行测试时，请求头内容格式为 x- www-form-urlencoded ，因此在前端 demo 中也用的这种格式，但发现无法写入数据，改为 json 后成功写入

2. 学习 D 3.js 数据可视化设计
使用 d3 练习画了一个笑脸和一个花瓣
