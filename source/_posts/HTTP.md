---
title: HTTP
date: 2018-08-12 21:31:15
tags:
---
### HTTP请求
HTTP请求由四个部分组成，格式如下  

* 1 动词 路径 协议/版本  
* 2 key1: value1  
* 2 key2: value1  
* 2 key3: value1  
* 2 Content-Type: application/x-www-form-urlencoded  
* 2 Host: www.baidu.com  
* 2 User-Agent: curl/7.54.0  
* 3  
* 4 要上传的数据  
> 1. 前三个部分是一定有的，有没有第四部分取决于有没有需要上传数据.  
> 2. 第三部分永远都是一个回车，作用是把第二部分和第四部分区分开.
> 3. 动词有 GET（获取） POST（新增或上传） PUT（整体更新） PATCH（局部更新） DELETE（删除） HEAD OPTIONS 等.
> 4. 路径包含[查询参数]但不包含[锚点].
> 5. 如果没有写路径，，默认路径为'/'.
> 6. 第 2 部分中的 Content-Type 标注了第 4 部分的格式.

### 如何用Chrome开发者工具查看 HTTP 请求内容  
1. 在任意Chrom页面按下"Ctrl+Shift+i"，进入如下页面,点击"Network"  
![network](https://raw.githubusercontent.com/fruittooth/blog-generator/master/images/http/network.png)
2. 在上方地址栏输入任意网址并进入，得到如下结果，选择并点击第一个'GET请求'  
![get](https://raw.githubusercontent.com/fruittooth/blog-generator/master/images/http/http3.png)
3. 展开右侧的'Headers'下的'Request Hearders',**点击旁边的'view source'**,  
![view source](https://raw.githubusercontent.com/fruittooth/blog-generator/master/images/http/HTTP4.png)  
4. 然后我们就能看到这个请求的前三部分内容了。  
5. 如果有请求的第四部分，那么在 FormData 或 Payload 里面可以看到  
------
### HTTP响应  
HTTP响应由四部分组成，格式如下


* 1 协议/版本号 状态码 状态解释  
* 2 key1: value1  
* 2 key2: value1  
* 2 key3: value1  
* 2 Content-Length: xxxxx  
* 2 Content-Type: text/html    
* 3  
* 4 要下载的内容  
> 1. 状态码是服务器对浏览器的回应，表示服务器当前响应状态。
> 2. 第 2 部分中的 Content-Length 标注了第 4 部分大小
> 3. 第 2 部分中的 Content-Type 标注了第 4 部分的格式
> 4. 第 2 部分中的 Content-Type 遵循 MIME 规范

### 如何用Chrome开发者工具查看 HTTP 响应内容  
1. 在任意Chrom页面按下"Ctrl+Shift+i"，进入如下页面,点击"Network"  
![network](https://raw.githubusercontent.com/fruittooth/blog-generator/master/images/http/network.png)
2. 在上方地址栏输入任意网址并进入，得到如下结果，选择并点击第一个'GET请求'  
![get](https://raw.githubusercontent.com/fruittooth/blog-generator/master/images/http/http3.png)
3. 展开右侧的'Headers'下的'Response Headers'，**点击旁边的'view source'**,
![](https://raw.githubusercontent.com/fruittooth/blog-generator/master/images/http/HTTP5.png)
4. 然后我们就能看到这个响应的内容了

### 'curl'命令  
'curl'命令可以通过命令行的方式,执行Http请求。通过curl命令，我们可以进行Http请求，访问页面，并且可以通过增加命令参数查看到请求和对应响应的详细内容。
* 访问指定页面时比如百度首页: curl -- "https://www.baidu.com"
* 查看详细的请求和响应内容: curl -v --"https://www.baidu.com"
* 默认请求方式为'GET',需要修改为其他方式，如'POST': curl -v -x POST -- "https://www.baidu.com",请求方式必须大写
* 在'HTTP header'添加信息；curl -H 'xxxxxxxx' -- "https://www.baidu.com"
* 向服务器上传数据:curl -d "aaaaaaaaaa" -- "https://www.baidu.com"
* 当我们想通过POST向服务器上传数据并查看详细的请求和响应内容时使用命令:curl -x POST -v -d "aaaaaaa" -- "https://www.baidu.com"