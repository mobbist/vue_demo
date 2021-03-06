# 实例 #
## 模板层 #

```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title></title>
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
<script type="text/javascript" src="./vue.js"></script>
</head>
<body>
    <!-- 模板 V-->
    <div id="demo">
      <!-- 期望的数据替代符 -->
      {{message}}
      <div v-on:click="chickHandle" >触发事件</div>
    </div>
</body>
</html>
```
## 模板层 #
```
<script type="text/javascript">
  // 数据  M
  let obj = {
    message :"hello"
  }

  //需要vue(VM)来把模板 V和数据M联系起来,
  var vm = new Vue({    //创建一个vue的实例,里面需要传入一个对象
      el:"#demo",   //定义模板的element, 需要把html中那个部分做为vue的模板,选择器
      data: obj,     //定义所要使用到的数据,  对象格式
      methods:{      //定义模板下的事件处理函数,统一进行管理
        chickHandle:function(){
          console.log("1");
        }
      }
  });
```

<p>每个vue的实例都会代理data对象里所有的属性, 这些被代理的属性是响应的, 新添加的属性不具有响应功能, 改变后不会更新视图</p>
<p>vue实例自身也会有函数, $开头 vm.$data 获得数据    vm.$el  获得模板</p>

  ## vue是声明式渲染 #

  > 命令式: 需要以具体代码表达在哪里(where) 做什么(what) 如何实现(how)
  ```
    var arr = [1,2,3,4,5]  //求数组中每一项的倍数, 并放在另一个数组中
    var newArr = [] //我需要一个新的数据
    for(var i=0;i<arr.length;i++){
      newArr.push(arr[i]*2)  //并开启一个for循环, 循环遍历数组中的每个值并计算, 再添加到一个新数组中
    }
  ```
  <p>这些过程都不可少, 要确切命令函数如何循环, 如何添加</P>

  > 声明式: 只需要声明在哪里(where) 做什么(what) 无需关心如何实现(how)
  ```
  //使用map函数
  var newArr2 = arr.map(function(item){
    return item*2
  })
  ```
  <p>我无需关心数据是怎么循环的, 我只要告诉函数, 给我返回倍数就行了</p>


</script>
</html>
