# TypeScript面试题

* 1、TypeScript与JavaScript的区别是什么？

```text
TypeScript是JavaScript的超集，它扩展了JavaScript，主要区别包括：

类型系统：TypeScript提供静态类型检查
面向对象特性：提供接口、泛型、枚举等特性
开发工具支持：更好的IDE支持，包括代码补全、重构等
及早发现错误：在编译时就能发现潜在问题
JavaScript互操作性：可以逐步将JavaScript代码迁移到TypeScript
```

* 2、TypeScript中的基本类型有哪些？

```text
TypeScript包含以下基本类型：

基础类型：
number：数字
string：字符串
boolean：布尔值
null和undefined
void：通常用于函数返回值
any：任意类型
never：永不存在的值的类型

对象类型：
object：对象类型
array：数组类型
tuple：元组类型

```

* 3、什么是泛型？为什么要使用泛型？

```text
泛型是一种在定义函数、接口或类时不预先指定具体类型，而在使用时再指定类型的特性。

优点：
代码复用
类型安全
减少冗余代码
```

* 4、TypeScript中如何实现接口继承？
```text
接口继承允许我们从一个接口复制成员到另一个接口，实现代码重用。
```

* 5、如何在TypeScript中处理异步操作？
```text
TypeScript完全支持现代JavaScript的异步特性，包括Promise、async/await等。
```

* 6、type 和 interface 共同和区别，如何选择？
```text
（1）共同：都能描述一个对象结构、都能被 class 实现、都能被扩展
（2）区别：type 可以声明基础类型、type 有联合类型和交差类型、type 可以被 typeof 赋值
（3）选择：能用 interface 就尽量用 interface，除非必须用 type 的时候才用 type
```

* 7、枚举（enum）是什么？
```text
枚举是一种对数字值集合进行命名的方式。它们可以增加代码的可读性，并提供一种便捷的方式来使用一组有意义的常量。
```

* 8、unknown 和 any 区别？
```text
unknown 是更安全的 any：
any 任何类型，会忽略语法检查
unknown 不可预知的类型，不会忽略语法检查（这就是最大区别）
```

* 9、keyof 和 typeof 有什么区别？
```text
typeof 是 JS 基础用法，用于获取类型。
keyof 是 TS 语法，用于获取所有 key 的类型。
```

* 10、数组 Array 和元组 Tuple 的区别是什么？

```text
数组元素只能有一种类型，元祖元素可以有多种类型。
```
