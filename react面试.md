## react的生命周期
   # 挂载阶段
     constructor() 
        constructor()中完成了React数据的初始化，它接受两个参数：props和context，
        当想在函数内部使用这两个参数时，需使用super()传入这两个参数。
        注意：只要使用了constructor()就必须写super(),否则会导致this指向错误。
     render 
     componentDidMount
     
         组件第一次渲染完成，此时dom节点已经生成，可以在这里调用ajax请求，返回数据setState后组件会重新渲染
        
    # 更新阶段
    
     shouldComponentUpdate
            主要用于性能优化(部分更新)
            唯一用于控制组件重新渲染的生命周期，由于在react中，setState以后，state发生变化，组件会进入重新渲染的流程，
            在这里return false可以阻止组件的更新
            因为react父组件的重新渲染会导致其所有子组件的重新渲染，这个时候其实我们是不需要所有子组件都跟着重新渲染的，
            因此需要在子组件的该生命周期中做判断
     render()
        render函数会插入jsx生成的dom结构，react会生成一份虚拟dom树，在每一次组件更新时，
        在此react会通过其diff算法比较更新前后的新旧DOM树，比较以后，找到最小的有差异的DOM节点，并重新渲染
      componentDidUpdate() 更新阶段
    #销毁阶段
     componentWillUnmount
        组件的销毁
        清除计时器，长链接等

### componentDidMount 这个生命周期里做了哪些逻辑

### Hooks 的有什么用 ，api怎么用
   作用：为无状态组件提供类似Class类组件的特性，有state 生命周期等

   useState,useEffect,useRefs useContext,useReducer,uesCallBack

## useEffect(()=>{
           相当于componentDidMount
       return (){
            相当于componentWillUnmount
       }
   },[更新阶段]) 只传一个空数组相当于constructor


   ## useContext 的作用
      在无状态组件中创建上下文，count=useContext(默认值)，解决进父子组件嵌套传值问题

## useState 的作用
   可以在函数组件中添加state而不必转换成class组件

## react 父子传值
  1 父传子：自定义属性，子组件通过props接收，     子传父：通过自定义事件传，props.父组件的自定义事件的属性(值)
  2 context(上下文)  const XX=React.createContext()
                     <xx.Provider value={{name:123}}><子组件A/></xx.Provider>
                     A.contextType=XX
                     在子组件中使用this.context.name使用它
  3 使用redux

## react 权限管理怎么做
   
   包括：资源（路由级）权限、操作（按钮级）权限，以及登录后用户级别的权限分配
         后端权限主要是对用户的每个请求进行权限验证，是否有这该权限。
         前端权限主要是对不同用户显示不同的模块，及对应模块的操作按钮等控制（隐藏或禁用）。   
   总结一下，其实前端在做权限控制的时候，依赖于后端 API 返回的配置信息，所以在权限设计，路由设计，
   数据结构设计的时候，前后端一定要约定好。

## HoC 高阶组件(函数)
  一种设计模式
    定义：  它就是一个方法，一个接收一个组件作为参数，返回一个增强的组件的方法
    HOC能够实现：
        1. 代码复用，代码模块化

        2. 渲染劫持, 操作state

        3. Props 增删改
    使用场景
            操纵 props
            通过 ref 访问组件实例
            组件状态提升
            用其他元素包装组件
    使用高阶组件遇到的问题
      当使用高阶组件包裹原始组件，返回的新组件会丢失原始组件的所有静态方法
    解决方案：使用hoist-non-react-statics来帮你自动处理，它会自动拷贝所有非React的静态方法；
## 封装过哪些组件，怎么实现的？
    vue组件封装
            建立组件的模板，先把架子搭起来，写写样式，考虑你的组件的基本逻辑
            然后在引用得组件中 用import引入组件
            通过component定义组件名称
            在把组件以标签的形式写出来。

    react组件封装

            创建一个react文件 , 搭建模板
            把组件内的内容写清楚
            使用export 把组件曝光
            使用import把组件导入
## react 的优缺点
   缺点
       react只是mvc框架中的v 缺乏redux react-router 
       不适合单独做一个完整的框架
   优点
     1,React速度很快
           它并不直接对DOM进行操作，引入了一个叫做虚拟DOM的概念，安插在javascript逻辑和实际的DOM之间，性能好
     2、跨浏览器兼容
           虚拟DOM帮助我们解决了跨浏览器问题，它为我们提供了标准化的API，甚至在IE8中都是没问题的。

     3、一切都是component：
           代码更加模块化，重用代码更容易，可维护性高。

     4、单向数据流
        Flux是一个用于在JavaScript应用中创建单向数据层的架构，它随着React视图库的开发而被Facebook概念化。

     5、同构、纯粹的javascript
        因为搜索引擎的爬虫程序依赖的是服务端响应而不是JavaScript的执行，预渲染你的应用有助于搜索引擎优化。

     6、兼容性好
## 为什么说react 一切皆是组件
    react是mvc中视图层v基于组件开发的
    
## 调用setState发生了什么
```
   （1）代码中调用 setState 函数之后，React 会将传入的参数对象与组件当前的状态合并，然后触发所谓的调和过程（Reconciliation）。
   （2）经过调和过程，React 会以相对高效的方式根据新的状态构建 React 元素树并且着手重新渲染整个 UI 界面；
   （3）在 React 得到元素树之后，React 会自动计算出新的树与老树的节点差异，然后根据差异对界面进行最小化重渲染；
   （4）在差异计算算法中，React 能够相对精确地知道哪些位置发生了改变以及应该如何改变，这就保证了按需更新，而不是全部重新渲染。
```


### react性能优化
   1,属性传递优化
       在consturctor里面进行事件函数的this指向的绑定
   2 ① shouldComponentUpdate(nextProps, nextState)：

    根据React组件的生命周期可以知道，组件在每次更新状态时都会执行shouldComponentUpdate函数，
    为了减少额外渲染，可以在该函数内对当前的props/state与nextProps/nextState进行比较，
    如果有一致的props/state则返回fasle说明不用重新渲染该组件，以减少重新渲染造成的性能浪费。

     ② React.PureComponent 替换 React.Component：
       在使用shouldComponentUpdate函数比较前后的props/state是否一致时，
       通常会涉及到深层或浅层的比较，在React默认进行的浅层比较中，
       可以使用React.PureComponent让组件根据传来的数据进行渲染而不是全部数据的渲染，
       这比自己写shouldComponentUpdate函数进行比较来的简单且性能更好
       ，但只适用于组件只根据传进来的数据进行渲染而没有内部状态时使用，可以最大限度的提升性能。

###  react 怎么做登入鉴权的呢
   在封装的axios请求拦截器中设置config.headers.Authorization = localStorage.getItem('token')
   在登入的时侯判断token是否存在，不存在则redirect重定向到登入页面
   
## 当token长时间失效时，怎么办？
     token失效时，后端回返回一个信息，在封装axios的响应拦截器中进行判断，
     删除过期的localStorage 然后通过window.location.reloud(),重新掉接口向后端调取接口
     

   
### rem 

   dpr = 屏幕像素(px) / 物理尺寸
   dpr = 2  二倍屏
   dpr = 3  三倍屏

   移动端布局：vw/vh，flexible，rem（最常用）

   rem：相对html标签的根字体大小，倍数关系
   em：相对于父级字体的大小，倍数关系
   px：绝对单位

   目标：10rem等于满屏
   做法：把当前页面的根字体的大小等于当前屏幕宽度的1/10
   第一步获取html标签dom对象 oHTML
   第二步通过js获取当前屏幕的宽度 w（单位是px）
   第三步，oHTML.fontSize = w*0.1 + 'px'
   原理：等比缩放

   建议在vscode安装一个cssrem的插件，它的作用是自动帮我把px单位转化成rem单位。
   它需要进行基准单位设置，设置成75（1rem=75px）


## react 有状态组件，无状态组件是什么
        
### 通信

```
父子通信
1. 父组件通过 props 传递数据给子组件，子组件通过调用父组件传来的函数传递数据给父组件，
这两种方式是最常用的父子通信实现办法
2.这种父子通信方式也就是典型的单向数据流，父组件通过props 传递数据，子组件不能直接修改props ，
而是必须通过调用父组件函数的方式告知父组件修改数据

兄弟组件通信：
对于这种情况可以通过共同的父组件来管理状态和事件函数，
比如说其中一个兄弟组件调用父组件传递过来的事件函数修改父组件中的状态，然后父组件将状态给另一个兄弟组件

跨多层次组件通信：
如果你使用16.3 以上版本的话，对于这种情况可以使用 Context API

任意组件:
这种方式可以通过Redux 或者 Event Bus 解决，另外如果你不怕麻烦的话，可以使用这种方式解决上述所有的通信情况 

```
### react 中的异步请求在哪个生命周期中进行，为什么
    componentDidMount,
    因为在这个生命周期里真实的dom已经渲染了，你要获取外部数据并加载到组件上，
    只能在组件"已经"挂载到真实的网页上才能作这事情，其它情况你是加载不到组件的。
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
    
   
 