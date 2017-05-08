# vue 是什么 #

>构建用户界面的渐进式框架,只关注视图层

## 渐进式框架 #
>如果只想用vue做一些模板引擎的使用,只做渲染, 把数据渲染到试图中, 那么只用vue就可以了<br>
>如果要把界面分N多个小模块,可以使用vue的组件系统<br>
>如果想做单页应用, SPA, 可以使用vue的路由系统<br>
>如果当组件过多, 希望共享数据的, 可以使用vue的状态管理<br>
>如果用构建工具, 去打包的...<br>
>渐进式框架就是要用到那一块功能, 就可以只使用某块功能就可以了, 不需要全部都用上. 没有强制性的概念.

## 只关注V层 #

### vue中的两个核心点 #
  1.  响应的数据绑定: 
    当拿到数据以后,是希望展示到界面中的, 当数据发生改变, 视图就会自动更新
  ```
  "use strict"
  let data = {   //定义的数据
    message: "hello, vue"
  }
  ```
  创建一个vm的实例
  ```
  var  vm = new Vue({
    el:"#demo",   //挂载元素
    data:data
  })
  ```
  当我再控制台上输入  vm.message = "hello, mobb" 的话, 视图会响应做出改变, 这就是响应的数据绑定

  >当数据发生改变   ->  自动更新视图
  >利用Object.defineProperty 中的setter/getter 代理数据, 监控对数据的操作 (不兼容IE8)

  2. 组合的视图组件
  UI页面映射为组件树
  划分组件可维护,  可重用  可测试


## 虚拟dom: #
>运行JS的速度是很快的, 大量的操作dom就会很慢, <br>传统更新数据渲染页面是 当数据发生改变时, 会拼写结构, 用innerHTML一次性再渲染<br>
>这样会操作大量的dom , 因为我只改变了某个地方, 但是却是整个渲染了一遍, <br>vue中使用了虚拟dom,只会渲染数据发生改变的地方, 大大提高了性能


## vue渲染过程: #
  1. 首先先有模板:
      ```
        <ul id="my-id">
              <li v-for="item in list" >{{item}}</li>
        </ul>
      ```
  2. 然后内部会调用渲染函数: createElement
      ```
      createElement({
          "ul",   //节点标签名
          //标签上的属性, 用对象储存键值对
          {
            attr:{
              id:"my-id"
            }
          },
          //该节点的子节点
          {
            createElement("li",1),
            createElement("li",2),
            createElement("li",3),
          }
      })
      ```
  3. 然后会调用render, 生成虚拟dom树,本质就是一个嵌套的对象
      ```
      VNode
        child:undefined,
        children:Array[3],
          0:VNode,
          1:VNode,
          2:VNode
          ...
      ```
  4. 最后生成真正的dom树
      ```
        <ul>
            <li>1</li>
            <li>2</li>
            <li>3</li>
        <ul>
      ```


## MVVM模式 #
>  M:   Model        数据模型  <br>
>  V:   View         视图模板  <br>
>  MV:  view-model   视图模型 (联系M和V, 监听数据发生变化更新视图)
