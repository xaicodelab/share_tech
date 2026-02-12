# VUE面试题

* 1、Vue3的主要新特性是什么？

```text
VUE的核心特性是数据驱动（MVVM)，MVVM表示的是 Model-View-ViewModel：
Model：模型层，负责处理业务逻辑以及和服务器端进行交互
View：视图层：负责将数据模型转化为UI展示出来，可以简单的理解为HTML页面
ViewModel：视图模型层，用来连接Model和View，是Model和View之间的通信桥梁

而Vue 3 的新特性包括：
Composition API：提供更灵活的代码组织方式。
性能优化：使用 Proxy 实现响应式，性能更好。
Tree-shaking：支持按需引入，减小打包体积。
TypeScript 支持：对 TypeScript 的支持更好。
Fragment、Teleport、Suspense：新增内置组件。
```

* 2、什么是Composition API（组合式API）？
```text
Composition API 是 Vue 3 引入的新特性，允许将逻辑组织为可复用的函数。
```

* 3、Vue 3 中的 setup 函数是什么？
```text
setup 是 Composition API 的入口函数，在组件创建之前执行。
```

* 4、Vue 3 中的 ref 和 reactive 有什么区别？
```text
ref：用于定义基本类型的响应式数据，通过 .value 访问。
reactive：用于定义对象类型的响应式数据。
```

* 5、Vue 3 中的 toRef 和 toRefs 是什么？
```text
toRef：将对象的某个属性转换为 ref。
toRefs：将整个响应式对象的所有属性转换为 ref。
```

* 6、v-show与v-if的区别？
```text
控制手段：v-show隐藏则是为该元素添加css--display:none，dom元素依旧还在。v-if显示隐藏是将dom元素整个添加或删除
编译过程：v-if切换有一个局部编译/卸载的过程，切换过程中合适地销毁和重建内部的事件监听和子组件；v-show只是简单的基于css切换
编译条件：v-if是真正的条件渲染，它会确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建。只有渲染条件为假时，并不做操作，直到为真才渲染
```

* 7、Vue组件之间的通信方式都有哪些？
```text
vue中8种常规的通信方案：
通过 props 传递
通过 $emit 触发自定义事件
使用 ref
EventBus
$parent 或$root
attrs 与 listeners
Provide 与 Inject
Vuex
```

* 8、Vue的生命周期有哪些？
```text
Vue生命周期总共可以分为8个阶段：创建前后, 载入前后,更新前后,销毁前销毁后，以及一些特殊场景的生命周期
生命周期	描述
beforeCreate	组件实例被创建之初
created	组件实例已经完全创建
beforeMount	组件挂载之前
mounted	组件挂载到实例上去之后
beforeUpdate	组件数据发生变化，更新之前
updated	组件数据更新之后
beforeDestroy	组件实例销毁之前
destroyed	组件实例销毁之后
activated	keep-alive 缓存的组件激活时
deactivated	keep-alive 缓存的组件停用时调用
errorCaptured	捕获一个来自子孙组件的错误时被调用
```

* 9、Vue 3 中的 v-bind 和 v-model 有什么区别？
```text
v-bind：单向绑定，数据变化影响视图。
v-model：双向绑定，数据和视图相互影响。
```

* 10、Vue 3 中的 v-for 和 v-if 的优先级是什么？
```text
v-if 的优先级高于 v-for。
```
