
# 指令 #
> 是一种特殊的自定义行间属性,指令的职责就是当其表达式的值改变的时相应的将某些行为应用到dom上
## 在vue中, 指令以v-开头 #
  <p>v-on          绑定数据处理函数,简写为  @</p>
  <p>v-bind        动态绑定数据, 简写为     :</p>
  <p>v-text        更新数据, 会覆盖已有的结构</p>
  <p>v-html        可以解析数据中的HTML结构</p>
  <p>v-show        根据值的真假,切换元素的display的属性</p>
  <p>v-if          根据值的真假,切换元素会被销毁, 重建</p>
  <p>v-if-else     多条件判断, 为真渲染</p>
  <p>v-else        条件都不符合渲染</p>
  <p>v-for         基于源数据多次渲染元素或模板</p>
  <p>v-model       在表单控件元素上创建双向数据绑定</p>
  <p>v-pre         跳过元素和子元素的编译过程</p>
  <p>v-once        只渲染一次, 随后数据更新不重新渲染</p>
  <p>v-cloak       隐藏未编译的Mustache语法,  css中设置[v-cloak]{display:none}</p>V


