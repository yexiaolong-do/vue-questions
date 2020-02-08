谈一谈你对vue响应式原理的理解？  
一、vue中模型层（model）只是普通JS对象，修改它则更新视图（view），这种响应式会让状态管理变得非常简单且直观。  
二、把一个普通JS对象传给Vue实例的data选项，Vue将遍历此对象的所有属性，并使用Object.fefineProrerty把这些属性转化为getter/setter，用户看不到getter/setter，但是在内部它们让Ve追踪依赖，在属性被访问和修改时
   通知变化。每个组件实例都有相应的watcher实例对象，它会在组件渲染过程中把属性记录为依赖，之后当依赖项的setter被调用时，会通知watcher重新计算，从而致使它关联的组件得以更新。  
[响应原理](https://github.com/yexiaolong-do/vue-questions/new/master)
三、受现代JS的限制，Vue不能检测到对象属性的添加或删除，由于Vue会在初始化实例时对属性进行getter/setter转换，所以属性必须在data对象上存在才能让Vue转换它，这样它才是响应式。  
```vue
var vm = new Vue({
  data:{
    a:1
  }
})
//'vm.a'是响应的
vm.b=2
//'vm.b'是非响应的
```
Vue不允许在已经创建的实例上动态添加新的根级响应式属性（root-level reactive property），然而它可以使用Vue.set(object,key,value)方法将响应属性添加到嵌套的对象上。  
```vue
vue.set(vm.someObject,'b',2)
```
也可以使用vm.$set实例方法，这也是全局vue.set方法的别名。
```vue
this.$set(this.someObject,'b',2)
```
还可以创建一个新的对象，让它包含原对象的属性和新的属性。  
```vue
this.someObject = object.assign({},this.someObject,{a:1,b:2})
```
四、声明响应式属性  
  由于vue不允许动态添加根级响应式属性，所以必须在初始化根实例前声明根级响应式属性，哪怕只是一个空值。data对象就像组件状态的概要，提前声明所有响应式属性，可以让组件代码在以后阅读或其他开发人员阅读时更便于理解。  
五、异步更新队列  
  vue异步执行dom更新，只要观察到数据变化，vue将开启一个队列，并缓冲在同一事件循环中发生的所有数据改变，如果同一个watcher被多次触发，只会一次推入到队列中。
