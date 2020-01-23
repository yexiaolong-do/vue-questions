你怎么理解vue中的diff算法？
①diff算法是一种优化手段，将前后两个模块进行差异对比，修补（更新）差异的过程叫做patch(打补丁)  
 diff算法比较的是虚拟dom，简单的说就是新旧虚拟dom 的比较，如果有差异就以新的为准，然后再插入的真实的dom中，重新渲染  
 特点  
只会做同级比较，不做跨级比较
比较后几种情况
if (oldVnode === vnode)，他们的引用一致，可以认为没有变化。
if(oldVnode.text !== null && vnode.text !== null && oldVnode.text !== vnode.text)，文本节点的比较，需要修改，则会调用Node.textContent = vnode.text。
if( oldCh && ch && oldCh !== ch ), 两个节点都有子节点，而且它们不一样，这样我们会调用updateChildren函数比较子节点，这是diff的核心
else if (ch)，只有新的节点有子节点，调用createEle(vnode)，vnode.el已经引用了老的dom节点，createEle函数会在老dom节点上添加子节点。
else if (oldCh)，新节点没有子节点，老节点有子节点，直接删除老节点。
增加key会增加比较效率，详见[Mozilla](https://github.com/yexiaolong-do/vue-questions/blob/master/key%20in%20vue.md)  
②总结：  
尽量不要跨层级的修改dom  
在开发组件时，保持稳定的 DOM 结构会有助于性能的提升  
设置key可以让diff更高效  
