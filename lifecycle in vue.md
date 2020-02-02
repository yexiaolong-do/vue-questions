谈谈你对vue生命周期的理解？  
一、vue有六个生命周期，分别是beforecreate，created，beforemount，mounted，beforedestroy，destroyed。  
二、当vue的数据变更时，会触发两个生命周期钩子，beforeupdate，updata。  
三、在keep-alive中包裹的组件有两个特殊的钩子：actived，deactivated.  
四、生命周期详解  
  1.beforeCreate：在实例初始化之后，数据观测（data observe）和event/watcher事件配置之前被调用，这时无法访问data及props等数据；  
  2.created：在实例创建完成后被立即调用，此时实例已完成数据观测（data observer），属性和方法的运算，watch/event事件回调，挂载阶段还没开始，$el尚不可用。  
  3.beforemount:在挂载开始之前被调用，相关的render函数首次被调用。  
  4.mounted：实例被挂载后调用，这时el被新创建的vm.$el替换，若根实例挂载到了文档上的元素上，当mounted被调用时vm.$el也在文档内。注意mounted不会保证所有子组件一起挂载。  
  5.beforeupdata：数据更新时调用，发生在虚拟dom打补丁前，这时适合在更新前访问现有dom，如手动移除已添加的事件监听器。  
  6.updated：在数据变更导致的虚拟dom重新渲染和打补丁后，调用该钩子。当这个钩子被调用时，组件dom已更新，可执行依赖于dom的操作。多数情况下应在此期间更改状态。
  如需改变，最好使用watcher或计算属性取代。注意updated不会保证所有的子组件都能一起被重绘。  
  7.beforedestory：在实例销毁之前调用。在这时，实例仍可用。  
  8.destroyed：实例销毁后调用，这时vue实例的所有指令都被解绑，所有事件监听器被移除，所有子实例也被销毁。
  9.actived：被keep-alive缓存的组件激活时调用  
  10.deactived：被keep-alive缓存的组件停用时调用  
