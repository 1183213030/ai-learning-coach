# The Modern JavaScript Tutorial (JavaScript.info) Index

> **资料标识**：`src-javascript-info`  
> **级别**：`S1` (Authoritative Textbook & Engine Mechanism Guide)  
> **根地址**：[https://javascript.info](https://javascript.info)  
> **角色**：深度机制教材：执行上下文、闭包、原型链拓扑、异步事件循环、Promise A+ 规范及 V8 内存模型

---

## 模块篇目与精准章节映射

### 第 1 部分：JavaScript 语言核心 (The JavaScript Language)

#### 1. JavaScript 基础与类型机制
- 变量声明与提升机制: [Variables](https://javascript.info/variables)
- 数据类型与物理存储: [Data types](https://javascript.info/types)
- 类型转换规则 (ToPrimitive, ToString, ToNumber): [Type Conversions](https://javascript.info/type-conversions)
- 宽松与严格比较 (`==` vs `===`): [Comparisons](https://javascript.info/comparisons)

#### 2. 对象基础与内存管理
- 对象引用与按引用传递: [Object references and copying](https://javascript.info/object-copy)
- 垃圾回收机制 (GC Reachability 与代际假说): [Garbage collection](https://javascript.info/garbage-collection)
- 对象到原始值转换协议: [Object to primitive conversion](https://javascript.info/object-toprimitive)
- `this` 隐式绑定与丢失: [Object methods, "this"](https://javascript.info/object-methods)

#### 3. 函数进阶与闭包
- 执行上下文与词法环境 (Lexical Environment): [Variable scope, closure](https://javascript.info/closure)
- 全局对象与环境记录: [Global object](https://javascript.info/global-object)
- 函数柯里化与高阶函数: [Currying](https://javascript.info/currying-partials)
- 箭头函数的词法绑定特性: [Arrow functions revisited](https://javascript.info/arrow-functions)

#### 4. 原型与继承拓扑
- 原型继承机制 (`[[Prototype]]`): [Prototypal inheritance](https://javascript.info/prototype-inheritance)
- 函数 `F.prototype` 属性: [F.prototype](https://javascript.info/function-prototype)
- 原生原型与终点边界 (`Object.prototype.__proto__ === null`): [Native prototypes](https://javascript.info/native-prototypes)
- 原型方法与没有原型的纯字典对象: [Prototype methods, objects without __proto__](https://javascript.info/prototype-methods)

#### 5. 异步编程与 Promise 核心机制 (当前攻坚节点重点支撑)
- 回调地狱与控制反转: [Introduction: callbacks](https://javascript.info/callbacks)
- Promise 规范与状态机: [Promise](https://javascript.info/promise-basics)
- 链式调用与处理程序返回值解析: [Promises chaining](https://javascript.info/promise-chaining)
- 错误传播与未捕获异常捕获: [Error handling with promises](https://javascript.info/promise-error-handling)
- Promise 类静态方法 (`all`, `race`, `allSettled`, `any`): [Promise API](https://javascript.info/promise-api)
- 微任务队列与事件循环时序 (Microtasks): [Microtasks](https://javascript.info/microtask-queue)
- `async/await` 语法糖底层状态机: [Async/await](https://javascript.info/async-await)

#### 6. 进阶元编程
- Proxy 与 Reflect 拦截器陷阱: [Proxy and Reflect](https://javascript.info/proxy)
- 迭代器与生成器: [Generators](https://javascript.info/generators)
- 模块加载与作用域隔离: [Modules, introduction](https://javascript.info/modules-intro)

---

### 第 2 部分：浏览器环境与事件模型 (Browser: Document, Events, Interfaces)

#### 1. DOM 树与几何属性
- DOM 树结构与节点关系: [DOM tree](https://javascript.info/dom-nodes)
- 节点属性与特性差异 (Attributes vs Properties): [DOM attributes and properties](https://javascript.info/dom-attributes-and-properties)
- 元素坐标、滚动与视口尺寸计算: [Element size and scrolling](https://javascript.info/size-and-scroll)

#### 2. 事件驱动机制
- 浏览器事件派发流 (捕获 -> 目标 -> 冒泡): [Bubbling and capturing](https://javascript.info/bubbling-and-capturing)
- 高性能事件委托设计模式: [Event delegation](https://javascript.info/event-delegation)
- 事件调度时序与事件循环交织: [Event loop: microtasks and macrotasks](https://javascript.info/event-loop)

---

### 第 3 部分：网络与存储协议 (Network Requests & Storage)
- Fetch 核心协议与流式处理: [Fetch](https://javascript.info/fetch)
- 跨域资源共享 (CORS) 判定边界: [Fetch: Cross-Origin Requests](https://javascript.info/fetch-crossorigin)
- 本地存储与同源策略限制 (LocalStorage, SessionStorage, IndexedDB): [LocalStorage, sessionStorage](https://javascript.info/localstorage)
