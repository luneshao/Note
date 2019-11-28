# MongoDB 笔记

## 配置环境变量

1.将mongodb的bin文件路径拷贝到系统环境变量中的path下，可以在cmd中直接输入命令mongod开启服务。

## 连接数据库

1.mongod --dbpath dir

## 创建数据库

1.use mongoName 

'注意'：如果数据库内没有集合或文档，数据库会创建不成功。

2.use test

db.collectName.insert({"key": "value"});

## 查看数据库

1.show dbs  //查看有几个库

2.show collection   //查看有几个集合

2.db.collectName.find() //查看集合中的所有记录
