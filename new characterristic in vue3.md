你知道vue3有哪些新特性吗？它们会带来什么影响？  
一、vue的新特性：  
  1.更快  
  2.更小  
  3.更易于维护  
  4.更多原生支持  
  5.更易于开发使用  
  6.重写虚拟dom  
  7.优化插槽生成  
  8.静态树提升  
  9.基于Proxy的观察者机制  
二、更快的vue3  
  1.重写虚拟dom  
  2.优化插槽生成：在当前vue版本中，当父组件重新渲染时，其子组件也必须重新渲染，vue3中，可以单独重新渲染父组件及子组件  
  3.静态树提升：vue3的编译器能够检测到什么时静态组件，然后将其提升，降低了渲染成本；  
三、基于Proxy的观察者机制  
  vue现有版本是使用Object.defineProperty的getter和setter。vue3使用ES2015的Proxy作为观察者机制，消除了以前存在的警告，使速度甲苯，并节省了一半的内存开销。  
四、vue更小  
  现版本的vue在运行时（runtime）压缩后大20kb，新的核心运行时压缩后大概10kb，这将在很大程度上通过消除不使用的库（Tree Shaking）来实现。  
五、使其更具可维护性  
  vue3将带来更多的可维护源代码，它不仅会使用TypeScript，而且很多软件包将被解藕，使其内容更加模块化。  
六、更多的原生支持  
  运行时的内核将与平台无关，使得vue可以更容易的与任何平台（web、ios或android）一起使用。  
七、更易于开发使用  
  Observer模块已被解压到自己的包中，允许以新的方式使用。跟踪重新渲染的位置也会更容易。  