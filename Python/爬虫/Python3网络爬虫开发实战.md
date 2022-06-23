# 第一章：爬虫基础
## 1.1.HTTP基本原理
### http的请求过程
==请求== 主要分为四部分：请求方法、请求的网址、请求头和请求体。
==请求体：== 一般承载的内容是 POST 请求中的表单数据，GET 的请求体为空
常见的 Content-Type 和 POST 提交数据方式的关系：
| Content-Typ                      | POST 提交数据的方式 |
| -------------------------------- | ------------------- |
| application/x-www-from-urlencded | 表单数据            |
| multipart/form-data              | 表单文件上传        |
| application/json                 | 序列化 JSON 数据    |
| text/xml                         | XML 数据                    |

---
## 多进程和多线程
Python 多线程的用法：<https://setup.scrape.center/python-threading>  
Python 多进程的用法：<https://setup.scrape.center/python-multiprocessing>  

/git