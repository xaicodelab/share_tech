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

* 6、什么是条件类型？如何使用？
```text
条件类型是TypeScript中的高级类型特性，允许我们基于类型关系进行类型选择。
```

* 7、什么是映射类型？如何使用？
```text
映射类型允许我们从现有类型创建新类型，通过映射现有类型的每个属性。
```

* 8、什么是类型收窄（Type Narrowing）？
```text
类型收窄是TypeScript中缩小类型范围的过程，有多种方式可以实现类型收窄。
```

* 9、联合类型和交叉类型的区别是什么？
```text
联合类型和交叉类型是TypeScript中两种重要的类型组合方式。
```

* 10、TypeScript中的类型体操实战有哪些？

```html
// 类型体操是TypeScript中高级类型的实际应用
// 实现Pick类型
type MyPick<T, K extends keyof T> = {
    [P in K]: T[P];
};

// 实现Readonly类型
type MyReadonly<T> = {
    readonly [P in keyof T]: T[P];
};

// 实现深度Readonly
type DeepReadonly<T> = {
    readonly [P in keyof T]: T[P] extends object 
        ? DeepReadonly<T[P]> 
        : T[P];
};

// 实现Partial类型
type MyPartial<T> = {
    [P in keyof T]?: T[P];
};

// 实现Required类型
type MyRequired<T> = {
    [P in keyof T]-?: T[P];
};

// 实现Record类型
type MyRecord<K extends keyof any, T> = {
    [P in K]: T;
};

// 实现Exclude类型
type MyExclude<T, U> = T extends U ? never : T;

// 实现Extract类型
type MyExtract<T, U> = T extends U ? T : never;

// 实现ReturnType类型
type MyReturnType<T extends (...args: any) => any> = 
    T extends (...args: any) => infer R ? R : any;

// 实际应用示例
interface Todo {
    title: string;
    description: string;
    completed: boolean;
}

// 只读的Todo类型
type ReadonlyTodo = MyReadonly<Todo>;

// 可选的Todo类型
type PartialTodo = MyPartial<Todo>;

// 提取Todo中的字符串类型属性
type StringProps = MyExtract<keyof Todo, string>;
```
