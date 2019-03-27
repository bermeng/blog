# FAQ

## WebStorm设置git bash

> settings -&gt; tools -&gt; terminal -&gt; 在shell bash中填写git bash的sh.exe路径，并在最后加上参数 -login -i

## vue assets（动态资源）和static（纯静态资源）

* webpack资源处理规则

> * 相对URL被解析成一个模块依赖（使用url-loader和file-loader进行处理）
> * 无前缀URL会被看作相对URL
> * 前缀为~的URL会被当作模块请求
> * /assets/logo.png不会被处理
> * 为使webpack返回正确的资源路径，使用`require('./assets/logo.png')`，file-loader进行解析，返回处理过的URL

* 在static/下的文件不会被Webpack处理：它们使用相同的文件名，直接拷贝到最终的路径；使用绝对路径引用这些文件
* static文件夹下的文件会按照原本的结构放在网站根目录下

## **规范模块**

> * AMD 规范
>
>   异步加载模块规范；一般应用在浏览器端
>
> * CMD 规范
>
>   通用模块加载规范；一般用在浏览器端
>
> * CommonJS 规范
>
>   一个单独的文件就是一个模块；一般应用在服务端；同步方式加载模块
>
> * UMD规范
>
>   通用模块规范；用来支持AMD和CommonJS这两种不一致的规范

## **使用git clone码云上的项目报错**

> * 错误： Authentication failed for '[https://gitee.com/cochain/wallet](https://gitee.com/cochain/wallet)'
> * 解决：`git config --system --unset credential.helper`（取消凭证）
> * 再次设置凭证命令为：`git config --global credential.helper cache`

## **vue项目（wallet）添加markdown支持**

> ### **安装** vue-markdown-loader

| 包 | 说明 |
| :--- | :--- |
| markdown-it | 渲染markdown基本语法 |
| markdown-it-anchor | 为各级标题添加锚点 |
| markdown-it-container | 用于创建自定义的块级容器 |
| markdown-it-emoji | 渲染 emoji |
| markdown-it-table-of-contents | 自动生成目录 |

* package.json中配置依赖版本
* 根据官方文档配置quasar.conf.js文件

## **css的display**

* `display: block`：显示为块级元素；宽度、高度、内外边距都可控制
* `display: inline`：显示为内联元素；宽度、高度、内外边距不可改变
* `display: inline-block`：显示为内联块元素；同行显示，并可修改宽高，内外边距

## **css垂直居中方法**

* `padding`
* `line-height`：将行高设置为和块元素高度相同
* `position`和`transform`

  ```text
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  ```

* 偏移50% + 负margin值

  ```text
  .center {
  position: absolute;
  height: 100px;
  width: 100px;
  top: 50%;
  left: 50%;
  margin-top: -50px;
  margin-left: -50px;
  }
  ```

* flex弹性布局居中

## **负边距**

> 给一个**不定宽**的块级框设置正边距会使其宽度减小，设置负边距会使其宽度增加。而给一个**定宽**的块级框设置左负边距会使其左移，设置右负边距没有影响。 绝对定位的元素框，使用margin-top和margin-left来上下左右移动；margin-bottom和margin-right不会产生任何影响。

## vue的computed、methods、watch

* computed默认只有getter，若需要可以添加一个setter；当页面中数据依赖其他数据进行变化时，可以用之。
* computed和methods效果相同，但computed基于依赖进行缓存；methods每次调用都会执行一次
* 需要在数据变化时执行**异步操作或开销较大的操作**时，使用watch。
* [参考](https://cn.vuejs.org/v2/guide/computed)\*\*\*\*

## 大端存储、小端存储

* 大端：数据高字节保存在内存低地址处，低字节保存在内存高地址处。
* 小端：数据高字节保存在高地址处，低字节保存在低地址处。

## wallet前端调用后端服务测试CORS问题

> 请求不同源（**域、协议、端口**）时浏览器会发出**跨源HTTP请求**

### 解决

* 1.使用caddy做代理，配置cors

```text
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

* 2.关闭浏览器同源策略（chrome）

```text
 chrome.exe --user-data-dir="C:/Chrome dev session" --disable-web-security //win下
 google-chrome --user-data-dir="/tmp/Chrome dev session" --disable-web-security //linux下
```

* 3.Chrome插件：`Allow-Control-Allow-Origin:*`（未使用，待验证）

## CORS

* 1.简单请求（满足以下条件）
  * 请求方法：HEAD、GET、POST
  * 头信息为以下字段：Accept、Accept-Language、Content-Language、Last-Event-ID、Content-Type
  * 字段设置
    * access-control-allow-origin（必须）
    * access-control-allow-credentials（是否允许发送cookie；可选）
    * access-control-expose-headers（可选）
* 2.非简单请求（除以上字段，还包括两个特殊字段）
  * access-control-request-method（必须）
  * access-control-request-headers
* 与JSONP的比较

  > JSONP只支持get请求；CORS支持所有类型的HTTP请求。

## get和post

* get用来获取信息，请求数据附加在URL后
* post用来提交信息，提交的数据存放在HTTP窗体中
* 一些浏览器和服务器会限制URL长度
* 一些web服务器会限制post提交数据大小

## 普通函数和箭头函数区别

* 箭头函数没有自己的`this`,其按作用域链向上查找，指向最近一层作用域的`this`
* 箭头函数的this始终指向函数**定义时**的this，而**非执行时**
* `arguments`、`super`、`new.target`这三个变量在箭头函数中也是不存在的。指向其外层函数对应的变量。

## **后端缓存类型**

* 数据库型缓存：如redis
* 文件型缓存：数据临时存入本地文件
* 内存型缓存：将一些热点数据调入内存，提高访问速度

## **关于浏览器**

* webkit内核：Safari浏览器。由两个引擎构成，渲染引擎webcore，js引擎jscore，从KDE的KHTML和js的KJS衍生而来
* chromium引擎：webkit分支
* Trident：微软家的IE
* Gecko：Mozilla friefox
* presto：opera浏览器，已使用google的引擎（chromium，Blink）
* android 4.4以下版本webview是一个webkit浏览器内核
* crosswalk的webview只针对android平台
* ionic：混合移动应用开发框架
* armeabi：arm v5，很老的一个版本，缺少对浮点数计算的硬件支持

