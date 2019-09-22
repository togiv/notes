# h1大标题
## h2标题
### h3标题
#### h4标题
##### h5标题
###### h6标题

## 斜体和粗体
*斜体*

_这是另一种斜体标志_

**粗体**

__粗体__
## 无序列表    * + - 都可以
* 这是无序列表
+ 记得打空格
- it was time to go
    * 嵌套列表
    * 缩进
        * 再嵌套
        * 再缩进

## 有序列表   与数字无关
1. 按crtl+shift+p
1. 找到markdownyulan
1. 新建一个md文件，开始编写
    1. 写一个大标题
    1. 写一个小标题

## 图片
![图片的名字](./捕获4.PNG)
## markdown兼容html的格式，有特殊需求可以用html标签来编辑如：
<img src="./捕获4.png" width=200>

Format:自己看


## link
[百度](http://www.baidu.com)

## 引言

就像乔布斯所说
>Stay hungry,stay foolish

>求知若渴，虚心若愚

## inline code  内联代码 es6字符串

通过使用 `npm install` 去安装 `package.json` 中的包

## 代码块
一个简单的node http模块例子

```javascript
var http=require('http')
var server = http.createServer(function(req,res){
    res.writeHead(200,{"Content-Type","text/plain;
    charset=utf-8"})
    res.end()
})
//监听3000端口
server.listen(3000)
```

```python
def function():
    print('*'*30)
    pass
```

```html
<div class="d1">这是一个div</div>
```

## Task lists

- [x] 你好
- [x] 你好
- [x] 先跳过

## Tables    表格使用-和|画表格 :表示居中居左居右
## 8月支出情况
项目  | 金额
:---- | ----:
吃饭  |  20
玩    |  10


## 分割线
---   
---为分割线
***
***为分割线

___
——————三个下划线为分割线
- - -
也为分割线









 
