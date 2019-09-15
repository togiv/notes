# You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near
scrapy pipeline 文件如下：
```python
class JianshuPipeline(object):
    def __init__(self):
        data = {
            'host':'localhost',
            'port':3306,
            'user':'root',
            'password':'******',
            'database':'jianshu',
            'charset':'utf8mb4'
        }
        self.conn = pymysql.connect(**data)
        self.cursor = self.conn.cursor()
        self._sql = None
    def process_item(self, item, spider):
        self.cursor.execute(self.sql, (item['title'],item['author'],item['pub_time'],item['origin_url'],item['content'],item['read_count'],item['like_count'],item['word_count'],item['comment_count']))
        self.conn.commit()
        return item

    @property
    def sql(self):
        if not self._sql:
            self._sql =
             "insert into article2(title,author,                     pub_time,origin_url,content,read_count,          like_count,word_count,comment_count) values(%s,%s,%s,%s,%s,%d,%d,%d,%d)
                                "
            return self._sql
        return self._sql
```
item 文件如下
```python
class JianshuItem(scrapy.Item):
    title = scrapy.Field()
    author = scrapy.Field()
    pub_time = scrapy.Field()
    origin_url = scrapy.Field()
    content = scrapy.Field()
    read_count = scrapy.Field()
    like_count = scrapy.Field()
    word_count = scrapy.Field()
    comment_count = scrapy.Field()
```
数据存入mysql数据库之前没有错误，存mysql数据库报错：
### You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near...
初步怀疑数据库建表出错，用 `Navicat Premium` 重新建表之后继续报错，`Navicat Premium` 建表不会出错，给定的数据类型检查没有错误,建表出错问题排除。继续报错有可能是传入数据的时候出错，继续测试，将传参改为如下：
```python
self.cursor.execute(self.sql, ('测试用'，'测试用'，'测试用'，'20190101'，'测试用'，'测试用'，'测试用'，10，20，20，10，'测试用'，))
```
正常运行没有报错
现在来看只能是item传参时出错，在写入数据库之前打印各个参数的值发现均没有错误，各方面独自运行均没错，只能是结合的时候出错，找传参时名字有没有写错，果然发现爬虫文件`item`实例化的时候类的名字写错，写的时候是复制的，粘贴了上次类的名字，导致传参的时候参数不对，将爬虫文件`item`实例化时候类的名字改为`JianshuItem`，数据成功保存到数据库中

