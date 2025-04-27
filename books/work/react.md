# react

## react 哲学

### react 哲学的问题

问题： react开发包含了哪些步骤

问题： 如何将UI拆解为组件层级的结构

问题： 单一职责在react中的运用

问题： 如何构建静态版本

问题： 什么是react单向数据流

问题： 如何找出UI精简且完整的state表示

问题： 哪些不是state

问题： 什么是dry

问题： 为啥要找出绝对精简的state

问题： 如何 验证state应该被放置在哪里

问题: 交互函数放到哪里


### oreact 哲学的问题详情

##### 问题：react开发包含了哪些步骤

将UI拆解为组件层级的结构

构建静态版本

找出UI精简且完整的state表示

验证state应该被放置在哪里

添加反向数据路

重点是找出UI精简并且表示完整的state，单一功能原则，dry原则，单向数据流，数据不可变性。

##### 问题： 如何将UI拆解为组件层级的结构 

根据原型来拆分，ui设计是会考虑ui设计和交互方式

程序设计。根据单一功能原则决定是否要创建一个对象或函数，理想情况下一个react组件只完成一件事情，随着功能的增加和扩大， 拆分成更多的组件

CSS 思考你将把类选择器用于何处。（然而，组件并没有那么细的粒度。）

设计 思考你将如何组织布局的层级

##### 问题： 单一职责在react中的运用

Single Responsibility Principle,SRP是面向对象设计中的一个重要职责。核心思想是： 一个类应该只有一个职责，且这个职责应该被完全封装在这个类中。

在react中单一功能职责原则在组件中很好的运用。

对于一个组件，对外完成一个功能。这里面包含了很多的概念，对于功能拆分常见的有ui部分，数据获取部分，交互逻辑部分，这些都可以单独作为一个组件被开发。是否要做到这个粒度，需要根据当前的业务来看，如果已经开发的被复用，可以在重构过程进行拆分。

举例来说，对于一个通过用户接口获取用户信息并展示的组件，可以分成

用户组件

调用用户接口获取用户信息逻辑部分

用户信息展示的ui部分

交互部分

##### 问题： 如何构建静态版本

对着ui分层构建静态版本的代码，自上而下还是自下而上都可以。在简单的例子中，自上而下构建通常更简单；而在大型项目中，自下而上构建更简单。

##### 问题： 什么是react单向数据流

指的是组件间的数据传递方向，只能由父组件向子组件传递。反过来不能传递。如果子组件需要修改父组件中的数据，必须通过调用父组件传递下来的回调函数来实现，这个回调函数会在父组件中更新状态，然后再将新的状态或数据传递给子组件。

##### 问题： 如何找出UI精简且完整的state表示

为了使UI可交互，你需要用户更改潜在的数据结构。你将可以使用state进行实现。

考虑将state作为应用程序需要记住改变数据的最小集合。组织state最重要的一条原则是保持它DRY（不要自我重复）。计算出你应用程序需要的绝对精简的state表示，按需计算其它一切。举个例子，如果你正在构建一个购物列表，你可将他们在state中存储为数组。如果你同时想展示列表中物品数量，不需要将其另存为一个新的state。而是通过读取你数组的长度来实现。

通过列出改变数据的地方，来找出所有的可能的state

##### 问题： 哪些不是state

随着时间推移保持不变？如此，便不是state。

通过props从父组件传递？如此，便不是state

是否可以基于以存在于组件中的state或者props进行计算？如此，它肯定不是state!

##### 问题： 什么是dry

don't repeat yourself,避免重复
系统中的任何一块知识（逻辑或信息）都应该在一个系统内有且只有一个、唯一可信的“来源”或“表现形式“

##### 问题：为啥要找出绝对精简的state

开销

不必要的render

状态越少，追踪问题越简单

逻辑更聚合，更符合直觉

##### 问题： 如何 验证state应该被放置在哪里

验证哪个组件是通过改变state实现可响应的，或者拥有这个state。记住：React使用单向数据流，通过组件层级结构从父组件传递数据至子组件。

验证每一个基于特定state渲染的组件

寻找 它们最近并且共同的父组件-在层级结构中，一个凌驾于他们所有组件之上的组件。

决定state应该被放置于哪里：

通常情况下，你直接放置state与他们的共同的父组件。

你也可以将state放置于它们父组件的上层组件

如果你找不到一个合适来放这个state的地方，单独创建一个新的组件去管理这个state，并将它添加到它们父组件上层的某个地方。

##### 问题： 交互函数放到哪里

交互函数放到哪里和state相关，确定了state的位置，如果一个函数影响这个这个state，那么这个交互函数就应该被定义在这个函数的部分


## react 官网教程基本

### react 官网教程基本的问题

问题： 创建react应用的方式

问题： react中常用的ts类型

问题： 常见方法的ts知识

问题： 常见事件ts

问题： React 开发者工具

问题： React Compiler 介绍

问题： immer 进行state更新

问题： Object.freeze 介绍

问题： immer freeze和produce的原理，简单说说

问题：自己开发的produce的思路

问题：自己开发的produce的问题

symbo作为属性和普通的字符串有什么不同

问题：实际produce方法的原理

### react 官网教程基本的详情

##### 问题： 创建react应用的方式

- [Next.js 的 App Router](https://nextjs.org/docs)   是一个 React 框架，充分利用了 React 的架构，支持全栈 React 应用。 主要部署到node.js或serverless的托管平台，或者部署到你自己的服务器。

- [React Router](https://reactrouter.com/start/framework/installation)   可以与 Vite 结合创建一个全栈 React 框架，标准的web api 

- [Expo](https://expo.dev/)  让你可以创建支持真正原生 UI 的通用 Android、iOS 和 Web 应用  react native

- [从零开始构建 React 应用](https://zh-hans.react.dev/learn/build-a-react-app-from-scratch)

##### 问题： react中常用的ts类型

- 尝试阅读 @types/react   [DefinitelyTyped 的 React 目录中](https://github.com/DefinitelyTyped/DefinitelyTyped/blob/master/types/react/index.d.ts)

- Dom 事件 写独立的事件处理函数，需要明确定义函数参数的类型，React.ChangeEvent<HTMLInputElement>,完整列表可以在 [这里](https://github.com/DefinitelyTyped/DefinitelyTyped/blob/b580df54c0819ec9df62b0835a315dd48b8594a9/types/react/index.d.ts#L1247C1-L1373) 查看

- 子元素。 React.ReactNode 在JSX中作为子元素传递的所有可能类型的并集,React.ReactElement 它只包括JSX元素，而不包括js原始类型，如string或number

- 样式属性 React.CSSProperties

##### 问题： 常见方法的ts知识

useState,useContext在初始化不是唯一的泛型，需要使用时加问号，可以通过一个hook来排除控制。判断为空抛出错误

useReducer, reducer函数第二个参数是个数组(A extends AnyActionArg),表示个dispatch接受多个参数，useReducer<S,A>((prevState, actions:[A]))

useRef<T>,参数可以是T，T|null，T|undefined,当时undefiend不可以给null，主要是看元素上的ref如何？元素上的ref接收Ref<T>,RefCallback<T> | RefObject<T | null> | null,就是返回泛型或者null。所以是元素时默认值需要是null，或者在ref中写函数，使用undefined

##### 问题： 常见事件ts

事件常见的属性

currentTarget: 注册事件函数的元素

target: 触发事件的的元素，有可能target是currentTarge的子元素

##### 问题： React 开发者工具

使用 React 开发者工具检查 React components，编辑 props 和 state，并识别性能问题。

##### 问题： React Compiler 介绍

React Compiler 是一个处于 Beta 阶段的新的编译器。 它是一个仅在构建时使用的工具，可以自动优化你的 React 应用程序。它可以与纯 JavaScript 一起使用，并且了解 React 规则，因此你无需重写任何代码即可使用它。

##### 问题： immer 进行state更新

use-immer给出连个方法，userImmer和useImmerReduce，如果状态是嵌套的对象，使用immer修改起来很方便

useImmer返回的一个只读的状态值，和一个设置函数，一般会使用时，传递一个更新函数，函数接受原来的state，可以和immer的produce方法一样直接修改该对象，会返回新的基于修改后的值返回的新的不可变对象

useImmerReduce在useReduce基础上，将第一个参数，reducer，方法的使用produce包装，即reuder接受的状态是收到produce监控的值


##### 问题： Object.freeze 介绍

冻结整个对象的属性，每个属性的writable和configuable置为false，对象的preventExtension置为false。它是浅冻结


##### 问题： immer freeze和produce的原理，简单说说

用 Proxy 把“可变式写法”偷偷转成“不可变式结果”，并在完成后递归 Object.freeze 锁定对象——既让开发者写得舒服，又保证状态真不可变。

freeze通过Object.freeze方法，深度freeze，避免循环引用,判断是否为引用类型**obj!==null && typeof obj==='objject'**,遍历对象 const key of Object.keys(obj)

#### 问题：自己开发的produce的思路

produce有点类似于valtio通过递归proxy来代理整个对象。实现思路是每次访问对象实际是访问一个代理对象。一开始对根对象代理，Proxy(root,handlers),在handler中的get方法，如果访问的值是一个引用类型，继续对这个引用类型进行代理，Proxy(root[p],handlers),这个递归包裹在一个getProxy函数中，还有个参数changedInfo({changeData,parentProp}[])记录了父元素的建克隆和当前对象在父元素的键值 parentProp.在set方法中判断如果当前set的值不相等，那么进行回溯,清空changeInfo数组，进行回溯赋值。

#### 问题：自己开发的produce的问题

对当前对象克隆时，使用了对象扩展运算法，newObj={...obj}，这种方法不能够对数组生效。比较用了lodash的isEqual这是深度比较，是没有用的。采取了在get节点复制，而不是写入复制。没有写delete方法。在写入时每次都回溯来改变值，而不是在完成后进行一次回溯，没有冻结数据，返回不可变数据。

#### symbo作为属性和普通的字符串有什么不同

symbo是唯一的不会与用户定义的键值相冲突;大多数日常操作"for in","Object.keys","JSON.stringify"等不会枚举Symbol键，因此对调用着来说不可见

#### 问题：实际produce方法的原理

实际的immer中的实现，是通过在创建代理时，创建一个state对象，该对象有base（初始对象），copy（复制对象），modified，parent，记录对当前对象的修改，然后将当前对象向下传入下个递归。然后使用了symbol作为键值，DRAFT_STATE


Proxy的逻辑,每当get时，判断当前键值是否是DRAFT_STATE,如果是返回state（说明是内部访问）。如果不是说明访问原来对象的属性，判断当前对象是否改变没改变取原来的对象，改变了取copy；获取值，如果值是对象或者数组，继续递归代理。当set时，判断当前对象是否已经修改过，没修改过设置copy为浅克隆base。并且回溯parent一直浅克隆base为copy并且将parent的modified置为true。在进行set操作。deleteProperty代理和set是样的。

finalize函数是解决的写复制回溯需要修改多次parent。finalize参数是proxy。通过proxy获取state。判断是否修改没有修改就返回base，如果修改了，将result先置为copy。遍历改对象，若果值满足draft（说明获取过），返回递归的finalize。



## 保持组件纯粹

通过将组件按纯函数严格编写，以避免一些随着代码库的增长而出现的、令人困扰的 bug 以及不可预测的行为。但为了获得这些好处，你需要遵循一些规则。

## 保持组件纯粹的问题

问题： 纯函数是什么，在React中的具体表现

问题： 副作用是什么，在React中的具体表现

问题： React为何侧重于纯函数

问题： 哪些地方可能引发副作用

## 保持组件纯粹的详情

##### 问题： 纯函数是什么，在React中的具体表现

纯函数的特征：1)只负责自己的任务。不会更改函数调用前就已存在的对象或变量,2)输入相同，则输出相同.不符合纯函数的是函数有副作用。

React 便围绕着这个概念进行设计。**React 假设你编写的所有组件都是纯函数。**也就是说，对于相同的输入，你所编写的 React 组件必须总是返回相同的 JSX。

改变了预先存在的变量的值，称为突变，mutation。 纯函数不会改变函数作用域外的变量，或在函数调用前创建的对象--这会使函数变得不纯粹。

##### 问题： 副作用是什么，在React中的具体表现

和纯函数的特征想法的现象，副作用描述了函数会改变函数作用域外的变量或者函数调用前创建的对象--即这会使函数变得不纯粹。对React来说React渲染过程必须是纯粹的，相同的输入返回相同的jsx，也不改变在渲染前已经存在的对象或者变量，这会使它变得不纯粹。一般来说你不应期望你的组件会按照某个顺序来渲染。副作用的重点是在对外部的对象的影响，函数内部的改变是局部突变，内部突变是没有问题的。对于react来说渲染过程中的局部修改也是没有问题的。


##### 问题： React为何侧重于纯函数

1. 可预测性 相同的输入返回相同的结果，可以满足在不同环境上，例如在服务器上。

2. 可以安全的缓存。由于有相同的输入输出，react可以安全的将相同的输入结果缓存，跳过渲染。相同的输入可以用来作为判断，完成记忆化，跳过渲染和渲染移到worker等高级优化

3. 并发模式准备 react渲染过程中可能在后台暂停、回复和取消一次渲染。 

构建的每个 React 新特性都利用到了纯函数。从数据获取到动画再到性能，保持组件的纯粹可以充分释放 React 范式的能力。

##### 问题： 哪些地方可能引发副作用

更新屏幕、启动动画、更改数据，它们是额外发生的事情，和渲染过程无关。
在 React 中，副作用通常属于 事件处理程序。事件处理程序是 React 在你执行某些操作（如单击按钮）时运行的函数。即使事件处理程序是在你的组件 内部 定义的，它们也不会在渲染期间运行！ 因此事件处理程序无需是纯函数。
如果你用尽一切办法，仍无法为副作用找到合适的事件处理程序，你还可以调用组件中的 useEffect 方法将其附加到返回的 JSX 中。这会告诉 React 在渲染结束后执行它。然而，这种方法应该是你最后的手段。
如果可能，请尝试仅通过渲染过程来表达你的逻辑。你会惊讶于这能带给你多少好处！