# FAQ

## WebStorm设置git bash

> settings -&gt; tools -&gt; terminal -&gt; 在shell bash中填写git bash的sh.exe路径，并在最后加上参数 -login -i

## vue assets（动态资源）和static（纯静态资源）

#### webpack资源处理规则

* 相对URL被解析成一个模块依赖（使用url-loader和file-loader进行处理）
* 无前缀URL会被看作相对URL
* 前缀为~的URL会被当作模块请求
* /assets/logo.png不会被处理
* 为使webpack返回正确的资源路径，使用`require('./assets/logo.png')`，file-loader进行解析，返回处理过的URL
* 在static/下的文件不会被Webpack处理：它们使用相同的文件名，直接拷贝到最终的路径；使用绝对路径引用这些文件
* static文件夹下的文件会按照原本的结构放在网站根目录下

## 使用git clone码云上的项目报错

* 错误： Authentication failed for '[https://gitee.com/cochain/wallet](https://gitee.com/cochain/wallet)'
* 解决：`git config --system --unset credential.helper`（取消凭证）
* 再次设置凭证命令为：`git config --global credential.helper cache`

## wallet前端调用后端服务测试CORS问题

> 请求不同源（**域、协议、端口**）时浏览器会发出**跨源HTTP请求**

#### 解决

1. 使用caddy做代理，配置cors

```Bash
http://localhost:7070
 {
cors / {
  allowed_headers *
}
log / stdout "{upstream} {remote} - [{when}] \"{method} {uri} {proto}\" {status} {size}"
proxy / 
https://localhost:8080
 {
  insecure_skip_verify
}
}
```

2. 关闭浏览器同源策略（chrome）

```text
 chrome.exe --user-data-dir="C:/Chrome dev session" --disable-web-security //win下
 google-chrome --user-data-dir="/tmp/Chrome dev session" --disable-web-security //linux下
```

3. Chrome插件：``Allow-Control-Allow-Origin:*``

## CORS

1. 简单请求（满足以下条件）
  * 请求方法：HEAD、GET、POST
  * 头信息为以下字段：Accept、Accept-Language、Content-Language、Last-Event-ID、Content-Type
  * 字段设置
    * access-control-allow-origin（必须）
    * access-control-allow-credentials（是否允许发送cookie；可选）
    * access-control-expose-headers（可选）

2. 非简单请求（除以上字段，还包括两个特殊字段）
  * access-control-request-method（必须）
  * access-control-request-headers

3. 与JSONP的比较

> JSONP只支持get请求；CORS支持所有类型的HTTP请求。

## get和post

* get用来获取信息，请求数据附加在URL后
* post用来提交信息，提交的数据存放在HTTP窗体中
* 一些浏览器和服务器会限制URL长度
* 一些web服务器会限制post提交数据大小

## 控制台调试
> ``console.log()``：如果打印的是一个对象，则会保持对这个对象的引用。查看结果时，会读取该对象。所以有时会出现一种奇怪的现象，即，打印出一个对象后，为该对象添加新的属性时，查看原来打印的对象会出现最新添加的属性。 
