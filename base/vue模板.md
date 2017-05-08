
# 模板 #
## html模板: #
>基于dom的模板, 模板都是可解析的有效的html

  ### 插值 #
  文本:使用"Mustache"语法, 双大括号 {{value}} <br>
  作用: 替换实例上的属性值, 当值改变时,  插值内容会自动更新 <br>
  原生的HTML: 双大括号输出的是文本, 不会解析html,如果希望解析成html 则需要使用 v-html="html" <br>
   属性: 使用v-bind进行绑定, 可以响应变化  v-bind:custom="data" <br>
  使用javascript 表达式, 写简单的表达式,三目运算等等  <br>


## 字符串模板: #
> 有些时候是需要动态的拼写字符串
```
  var abc = 5;
  var str = "<div>hello{{abc}}</div>"  //注意;这里的根元素必须只有一个
  var vm = new Vue({
    el:"#demo",
    data:obj,
    template: str  //使用这个属性, 就把挂载点下的内容替换为该字符串
  })
```
> 还可以使用script片段
```
    <script type="x-template" id="temp">
       <div>hello{abc}</div>
    </script>
```
在template中, 替换为 #temp , 会自动找到该片段,有局限, 不能跨文件复用


## render 函数: #
>接近编译器的语法, html和字符串模板都会编译为render函数.
```
    var vm = new Vue({
    el:"#demo",
    data:obj,
    render(createElement){ //render函数接受一个参数
      return createElement(
        "ul",  //需要渲染的标签
        { //该标签上的属性
          class:{},     //绑定class,和v-bind:class一样的API, {isclass:true} ,对象形式的键值对
          style:{},     //绑定样式, 和v-bind:style一样的API,{fontSize:"50px"},对象形式的键值对
          attrs:{},     //自定义属性对象形式的键值对 {attr:123}
          domProps:{    //dom的属性
            innerHTML: "<li></li>"  //这里会对子元素进行替换, 慎用
          },
          on:{}    //和 v-on一样   
        },
        [ //生成子元素
          createElement("li",1) //第二个参数是内容
          createElement("li",2)
          createElement("li",3)   
        ]
      )
    }
  })
```

