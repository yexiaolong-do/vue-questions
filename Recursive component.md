什么是一个递归组件？  
一、组件在它的模板内可以递归地调用自己，只有当它有 name 选项时才可以。  
二、主要是实现一个信息的分类展示列表存在二级/三级的分类即树状结构  
三、示例：  
  首先创建一个List的递归组件  
```vue
<template>  
  <div>
    <div class="list-item v-for="(item,index) in list" :key="index">
      <div class="item-name>
        <span>{{item.name}}</span>
      </div>
      <div v-if="item.chilren" class="children-item">
        <list :list="item.children></list>
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    name: "List",
    props:{list:Arrar}
  }
</script>
```
  注意上面的代码我们用了List组件本身，完成后我们在外部父组件中使用List组件时，不管数据有多少嵌套关系，都可以实现自适应加载而不需要去层层嵌套了。  
```vue
<template>
  <div class="list-detail">
    <list :list="list"></list>
  </div>
</template>
<script>
import List from "./components/list";
export default {
  name: "parent",
  components: {List},
  data () {
    return {
      list:[{
        name:"经济",
        children:[{
          name:"如家",
          children:[{
            name:"上江路-如家"
          },
          {
            name:"望江路-如家"
          }]
        }，
        {
          name: "7天",
          children: [{
            name: "长江路-7天"
          },
          {
            name: "望江路-7天"
          }]
      }]
    }
  }
}
</script>
```
  类似与信息分类的展示我们都可以用递归组件解决。
