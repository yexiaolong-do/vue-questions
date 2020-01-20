# vue-questions
vue常见问题解答
1.v-if和v-for哪个优先级高？如果两个同时出现，应该怎么优化得到更好的性能？
①v-for的优先级高，但应尽量避免两者出现绑定在一个元素上；
②为避免两者同时出现，有以下两种处理方式：
·如是为了过滤一个列表中的项目(v-for="item in items" v-if="item.isActive"),可将item替换成一个计算属性，让其返回过滤后的列表；
·如果是为了避免徐然本来应该隐藏的列表(v-for="item in items" v-for="showItems"),这时可将v-if移动到容器元素上(v-for绑定的元素的的父元素)
