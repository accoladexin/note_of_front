# 1.了解jQuery中的Ajax

jQuery 中发起 Ajax 请求最常用的三个方法如下： 

1. $.get()
2. $.post()
3. $.ajax()



## 1.1 $.get()函数语法

```javascript
$.get(url, [data], [callback])//[]非必选项
```

其中，三个参数各自代表的含义如下：

![image-20211027205421471](Ajax%E4%B8%8EHttp.assets/image-20211027205421471.png)

不带参数的例子

```javasript
<button id="test">点击请求</button>

    <script src="../jquery.js"></script>
    <script>
        $(function() {
            $('#test').on('click', function() {
                $.get('http://www.liulongbin.top:3006/api/getbooks', function(res) {
                    consle.log(res); // 这里的 res 是服务器返回的数据
                    aler(res);
                })
            })
        })
    </script>
```

![image-20211027213159581](Ajax%E4%B8%8EHttp.assets/image-20211027213159581.png)



带参数的例子

```JavaScript
<script>
        $(function() {
            $('#test').on('click', function() {
                $.get('http://www.liulongbin.top:3006/api/getbooks', {
                    'id': 1
                }, function(res) {
                    consle.log(res); // 这里的 res 是服务器返回的数据
                    aler(res);
                })
            })
        })
    </script>
```



![image-20211027213422825](Ajax%E4%B8%8EHttp.assets/image-20211027213422825.png)

## 1.2  $post()函数的用法

$.post() 函数的语法如下

```JavaScript
$.post(url, [data], [callback])
```

![image-20211027213733377](Ajax%E4%B8%8EHttp.assets/image-20211027213733377.png)

同理函数

```
$.post(
'http://www.liulongbin.top:3006/api/addbook', // 请求的URL地址
{ bookname: '水浒传', author: '施耐庵', publisher: '上海图书出版社' }, // 提交的数据
function(res) { // 回调函数
console.log(res)
}
)
```

## 1.3 $ajax函数的用法

### 1.3.1 使用$.ajax()发起GET请求

使用 $.ajax() 发起 GET 请求时，只需要将 type 属性的值设置为 'GET' 即可：



````javascript
$.ajax({
type: 'GET', // 请求的方式
url: 'http://www.liulongbin.top:3006/api/getbooks', // 请求的 URL 地址
data: { id: 1 },// 这次请求要携带的数据
success: function(res) { // 请求成功之后的回调函数
console.log(res)
}
})
````

### 1.3.2 使用$.ajax()发起POST请求

```javascript
$.ajax({
type: 'POST', // 请求的方式
url: 'http://www.liulongbin.top:3006/api/addbook', // 请求的 URL 地址
data: { // 要提交给服务器的数据
bookname: '水浒传',
author: '施耐庵',
publisher: '上海图书出版社'
},
success: function(res) { // 请求成功之后的回调函数
console.log(res)
}
})
```

## 1.4 接口测试工具及使用方法

Postman

访问 PostMan 的官方下载网址 https://www.getpostman.com/downloads/，下载所需的安装程序后，直接安装即可

Get接口

![image-20211027215418966](Ajax%E4%B8%8EHttp.assets/image-20211027215418966.png)

post接口

![image-20211027215341333](Ajax%E4%B8%8EHttp.assets/image-20211027215341333.png)

























































.