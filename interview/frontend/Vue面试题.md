# VUE面试题

* 1、Vue 3 的主要新特性是什么？

```text
Vue 3 的主要新特性包括：

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

* 6、Vue 3 中的 v-model 有哪些变化？
```text
Vue 3 支持多个 v-model 绑定。
```

* 7、Vue 3 中的 computed 是什么？
```text
computed 用于定义计算属性。
```

* 8、Vue 3 中的 watch 如何监听多个数据？
```text
通过数组传入多个监听源。
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
