你好，我叫刘本翔，我做开发做了三年了，

我在过去的三年的里做过后台管理系统，电商网站，app,微信小程序，webApp,
其中的用到的技术栈有，vue,vuex,vue-router,vant-ui,element-ui,axios,
管理系统用的技术栈，react,redux,react-router,ant-design,还有第三方echart图表，moment插件等


    上家公司在上海，一个乐购家电app项目，我负责的是购物车模块和登入注册模块,在登入过程中对用户进行登入鉴权,
    对商品的增删改查，订单提交,主要用到的技术有vant-UI组件库,vuex状态管理数据
项目遇到的难点：接口联调过程中的后端返回的数据不是我想要的，
    但是我这边处理起来的很麻烦当时没想到怎么处理这个数据，0
    最后的解决办法就是后端筛选出来返回回来，
    还有一些因为使用了ui组件，有些样式不好调，
还有一个项目比较有印象，一个后台管理系统，用react做的，我
        负责的的是权限管理系统，用户的增删改查，这个就是要跟后端约定好我们需要哪些字段，
        通过拿回来的字段控制路由级别的或则是同一个组件上的某些按钮的显示与隐藏，
        在其中的过程中遇到了文件上传失败的问题，经过梳理代码，还有查找有关的文档，
        最后在axios的请求头里手动添加bundry这个字段，就解决了这个问题。


## 数组的操作方法

  会改变数组的方法：pop unShift shift push splice sort reverse 
  不会改变数组的方法：join slice concat

#### 防止注入攻击，安全方面的问题

 一 跨站脚本攻击（XSS攻击）
                攻击者往Web页面里插入恶意html代码，当用户浏览该页之时，嵌入其中Web里面的html代码会被执行
    xss常见的攻击方式：
                用户提交的数据未经处理，直接住注入到动态页面中
    危害：盗取各类用户帐号 ，企业数据，强制发送电子邮件，网站挂马	
    解决方案：不信赖用户输入，对特殊字符如”<”,”>”转义，或者是替换

小结：用户提交的时候 ，可能输入代码，存放到数据库
	  用户读取数据的时候，数据库中代码可能会执行

二 跨站请求伪造(CSRF攻击)
    跨站请求伪造(CSRF攻击)
	现象：有一个和官网一样的网站，篡改官网的提交的路径，或者cookie一起提交，
	导致提交数据流入外部网站 从而泄密
	
	解决方案：
		用户必须输入验证码，手机验证码...
		添加token 来进行二次校验 增强安全性
  
三：SQL注入攻击 
    验证用户名 和 密码相等的 sql 
	select * from 表名 where uName='{$uName}' and uPwd='{$uPwd}';
	select * from 表名 where uName='zhangsan' or 1='1' and uPwd='';
概念：攻击者将SQL命令插入到Web表单提交、输入域名、页面请求的查询字符串，
	  最终达到欺骗服务器执行恶意的SQL命令
危害： 任意登录系统 ，进行任意操作
解决： 1. 增加黑白名单验证  
			白：数据类型 长度 取值范围（js正则验证）.. 包含= ‘   ，终止请求
			黑：包含恶意内容拒绝请求
	   2. 安全监测 ，依靠各种安全漏洞的工具 来监测安全性
	   3. 防止敏感信息泄露 --》缩减用户 的权限

四 接口安全：
	传递数据的时候，把数据加密，到了后端解 密数据，正常入库
	数据crptyjs加密
	    加密 过程：

### 7.Promise理解

```
是什么？
promise是一个对象，从它可以获取异步操作的消息；承诺过一段时间会给你一个结果。
三种状态 pending(等待态)，fulfiled(成功态)，rejected(失败态)

特点：状态一旦改变，就不会再变。创造promise实例后，它会立即执行。

解决了什么问题？
回调地狱，代码难以维护
promise可以支持多个并发的请求，获取并发请求中的数据

有哪些方法？
.then(成功的回调)
.catch(失败的回调)
.all接收一个数组参数，里面的值最终都算返回Promise对象
.race的用法：谁跑的快，以谁为准执行回调


```
### 原型 原型链

 		实例对象访问属性或方法的原则：
			//先在实例中找，如果找不到，到原型对象下找，如果还找不到，向父类的原型对象中找，
            如果还找不到继续往上找，最后找到Object的原型对象 ，如果还没有返回 undefined


		//Object没有父类，因些Object.prototype.__proto__===null
		//console.log(Object.prototype.__proto__);//null
		
		//原型链：实例对象下有一个指针__proto__,这个指针指向构造函数的原型对象 ，
        原型对象 下也有一个__proto__指针，这个指针指向父类的原型对象 ，
        指针与指针之间形成了访问链条关系。这种形式就是一种原型链。
### new关键字做了什么
  
		1，健了一个空对象，将这个对象返回
		2，将构造函数中的this指向实例对象。
		3, 产生一个__proto__指针，将实例对象下的__proto__指针指向构造函数中的原型对象 
	
### SEO优化
   什么网页？
  视图 View + 模型数据 Model

BSR 客户端渲染(前后端分离)：视图与数据的组装是在客户端完成的
SSR 服务器渲染(前后端不分离)：视图和数据的组装是在服务端完成的


BSR的优势和劣势有哪些？
  前后端分离
  数据化应用，交互更加丰富
  前端工程师来讲价值更高
  SEO有严重劣势
  在ToB产品上应用更广泛

SSR的优势和劣势有哪些？
  前后端不分离,对后端的要求非常高
  有利于SEO
  对客户端的压力比较小，服务器压力较大
  在Toc产品上应用比较广泛



SEO：搜索引擎优化，让用户更多地找到你
SEO优化的原则：尽量减少js、css功能，尽可能多地使用静态html
SEO策略：官网、移动官网
  数据能用静态渲染，尽量使用渲染
  h1-h6  
  尽量不要都使用div
  html5语义化标签 header footer article nav aside
  加上title属性
  加上图片alt属性
  meta 元数据、关键词



Vue SSR的发展

  Next.js React的服务端渲染框架
  Nuxt.js Vue的服务端渲染框架

  只能依赖Node.js平台进行开发，核心库 vue-server-renderer。
  原理：使用vue-server-renderer在node.js服务端把Vue组件转化成静态HTML字符串，返回给客户端，数据与视图的组装也是发生在服务端。

Nuxt.js框架只作了解即可。
### 防抖，节流
    	1去抖：在一个时间段内，如果高频触发，不执行结果，当触发停下来后，才去获取结果，
				//在一个时间段内，只执行一次结果
		2节流：每隔一个时间段执行一次结果

       function dithering(callBack,ms){
			var t = null;
			// var istrue=true;
			return function(){//这里是事件处理程序，事件对象在这里传递
				// if(!istrue){
				// 	return;
				// }
				clearTimeout(t);
				// istrue=false;//
				var arg = arguments;//这个arguments是当前函数执行环境下的arguments
				t = setTimeout(function(){
					callBack.apply(this,arg);
					// istrue=true;
				}.bind(this),ms);
			}
		}
		document.getElementById("uname").oninput = dithering(function(eve){
			var e = eve || event;
			console.log(this.value,e);
		},1000);
### nodeJS

  常用的三个大模块    http  path  fs
  一般需要安装的依赖：
  express 
  mongoose  利用mongoose模块创建数据集合构建一个model，这个model对象上有增删改查的api
  var mongoose = require('mongoose')


    // 连接数据库
        mongoose.connect('mongodb://localhost/qf2006', {
        useNewUrlParser: true,
        useUnifiedTopology: true,
        useFindAndModify: false,
        useCreateIndex: true
        })

    // 获取数据库连接对象
    var connection = mongoose.connection

    connection.on('open', function() {
    console.log('数据库连接成功')
    })

    connection.on('error', function() {
    console.log('数据库连接失败')
    })
  用到的后端鉴权需要：jsonWebToken  生成一个token

  nodejs里面利用 var http = require('http'); 
                var server = http.createServer()创建一个nodeJs服务，
                    server.listen(port, function() {
                        console.log('server is running on 9000')
                    });
   fs.readFile() fs.writeFile可以对文件进行读写，还有复制，移动，还有一些其他的忘记了
   path模块提供了一些实用工具，用于处理文件和目录的路径。
        path.resolve()  path.dirname()
### 页面性能优化


  (1)优化图片资源的格式和大小
  (2)开启网络压缩
  (3)使用浏览器缓存
  (4)减少重定向请求
  (5)使用CDN存储静态资源
  (6)减少DNS查询次数
  (7)压缩css和js内容


### redux


       Redux三大原则

      ```
          唯一数据源：
              整个应用的state都被存储到一个状态树里面，并且这个状态树，只存在于唯一的store中
              
          state  保持只读状态：
                state是只读的，唯一改变state的方法就是触发action，action是一个用于描述以发生时间的普通对象
                
          数据改变只能通过纯函数来执行：
                使用纯函数来执行修改，为了描述action如何改变state的，你需要编写reducers
  
      Redux 由以下组件组成：

          **store：用来存储数据** 
          **reducer：真正的来管理数据**
          **actionCreators：创建action，交由reducer处理**
          **view： 用来使用数据，在这里，一般用react组件来充当**

      核心组件：
            **Provider  提供者  属性上通过store将数据派给容器组件**
            **connect    用于连接容器组件与UI组件**
            
            `connect() 返回一个函数，函数参数接收UI组件，返回容器组件`  
            connect(mapStateToProps,mapDispatchToProps)(ui组件)
            容器组件内部帮你做了 store.subscribe() 的方法订阅

    ：2.流程
            组件视图 通过 事件 发送 dispatch 派发action
            store 接收到 action , 把action和 oldState 当做参数发送给 reducers，
            reducers 接收 action和 oldState 通过计算返回新的 newState 给 store
            store 会把 state 重新渲染到组件内视图

   ```
   ### 4.vue前端性能优化

    ```
      代码层面的优化
      1.v-if和v-show场景的区分，v-show适用于頻繁的切换。
      2.路由懒加载
      3.图片懒加载
      4.v-for要加key
      4.computed和watch场景的区分，computed有缓存，watch适用于监听数据的回调。
      5.长列表的性能优化
      6.无线列表的优化 插件vue-virtual-scroll-list
      如果我们的组件只是纯展示数据：不会有其他变化，
      可以用object.freeze冻结数据，这样可以明显减少组件初始化的时间
      7.服务端渲染 seo  首页加载

      webpack层面
      1.按需引入第三方插件 babel-plugin-component
      2.对图片压缩 image-webpack-loader
      3.减少 ES6 转为 ES5 的冗余代码
      web技术层面的优化
      1.开启gzip 文件压缩
      2.浏览器缓存
      3.cdn加速，减小服务器的压力
    ```
### css3,新增属性
   边框 (Borders)
border-color    border-image    border-radius     box-shadow

文本 (Text effects)
text-shadowtext-overflowword-wrap

颜色 (Color)
 opacity    RGBA 

 ### html5新增的
      1. 语义化更好的内容标签（header,nav,footer,aside,article,section）
      3. 音频、视频API(audio,video)
      4. 画布(Canvas) API
      5. 地理(Geolocation) API
      6. 本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失；
      7. sessionStorage 的数据在浏览器关闭后自动删除
      8. 表单控件，calendar、date、time、email、url、search  
      9. 新的技术webworker, websocket, Geolocation
 