<!--
author: Jack.Spanrrows
date: 2018-02-12 
title: MongoDB-python的API手记
tags: python,mongo
category: Python3
status: publish
summary: MongoDB-python的API手记
-->

###----------------------------------python调用MongoDB--------------------------------------

###1.这里服务器环境是ubuntu16.04，使用apt安装mongo

###sudo apt-get install mongo-server

###2.安装python的mongo的模块

###sudo pip3.5 install pymongo

```
3.测试python驱动：

#coding=utf-8

#coding=utf-8

"""
测试python驱动
"""

#引用对应的包
import pymongo

#创建一个mongo客户端对象
client = pymongo.MongoClient("127.0.0.1",27017)
#获得mongoDB中的数据库对象
db = client.test_database
#在数据库中创建一个集合
collection = db.test_collectionTwo

#创建一条要加入数据库中的数据信息,json格式
post_data = {"username":"xiaohao","pwd":"123456",}

#进行数据的添加操作,inserted_id返回添加后的id编号信息
post_data_id = collection.insert_one(post_data).inserted_id

#展示一下插入的数据信息
print collection.find_one()

#打印当前数据库中所有集合的民称
print db.collection_names()

#打印当前集合中数据的信息
for item in collection.find():
    print item

#打印当前集合中数据的个数
print collection.count()

#进行find查询，并打印查询到的数据的条数
print collection.find({"username":"xiaohao"}).count()



```

###4.Aggregation Examples：mongoDB聚合练习


```
#coding=utf-8

'''
进行聚合aggregation 练习
'''

#引包
import pymongo

client = pymongo.MongoClient("127.0.0.1",27017)

db = client.aggregation_database

collection = db.aggregation_collection

collection.insert_many([
    {"username":"xiaohao01","pwd":"111"},
    {"username":"xiaohao02","pwd":"222"},
    {"username":"xiaohao03","pwd":"333"}
])


# for item in collection.find():
#     print item

#python中不含有son语法，需要使用son

from bson.son import SON

pipeline = [
    {"$unwind":"$pwd"},
    {"$group":{"_id":"pwd","count":{"$sum":1}}},
    {"$sort":SON([("count",-1),("_id",-1)])}
]

result = list(collection.aggregate(pipeline))

print result
```
