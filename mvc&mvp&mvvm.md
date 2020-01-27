谈谈你对MVC、MVP和MVVM的理解?  
一、mvc模式的意思是，软件可以分成三个部分：视图（view）即用户界面；控制器（controller）即业务逻辑；模型（model）即数据保存  
    三个部分之间的通信方式如下：
    ![mvc](https://github.com/yexiaolong-do/vue-questions/blob/master/img/mvc.png)  
    view传送指令到controller，controller完成业务逻辑后，要求Model改变状态，Model将更新的数据发送到View，用户得到反馈。所有通信都是单向的  
二、MVP模式将controller改名为Presenter，同时改变了通信方向。
    ![mvp](https://github.com/yexiaolong-do/vue-questions/blob/master/img/mvp.png)  
    各部分之间的通信都是双向的，view与model不发生联系，通过Presenter传递，view非常薄，不部署任何业务逻辑，被称为“被动视图”（Passive View），即没有任何主动性  
    而Presenter非常厚，所有逻辑都部署在那里。  
三、MVVM模式将Presenter改为View Model，基本上与MVP模式完全一致。  
    ![mvvp](https://github.com/yexiaolong-do/vue-questions/blob/master/img/mvvm.png)  
    唯一的区别是，它采用双向绑定（data-binding）：View的变动自动反应在view model，反之亦然。
