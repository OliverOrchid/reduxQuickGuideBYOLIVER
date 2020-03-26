# -Redux Guide BYOLIVER

## ***VOCABULARY***

```html
########################################################
reference  [ˈrefrəns] n. 参考手册，参照指南；参考书目；介绍信；证明书
active routes  激活的路由
selected tabs  选定的标签
spinners  加载动效
pagination controls  分页控件,分页器
ever-changing  adj. 不断变化的
No surprises. 没有什么好奇怪的

###########################################################
mutation  n. 突变,变异
matrix [ˈmeɪtrɪks] n. 矩阵; (细胞)基质；母体；子宫
metal matrix  金属模版
convention n. 惯例，习俗，不成文约定，常规
A is equivalent to B  A等效于B，等价于
assign  分配，指定，指派，赋值，亦可代指拷贝操作
communist n. 共产主义  adj.主产主义的

###########################################################
party n. 政党，党派，帮派
third party  第三方
communist party  共产党
party committee  党委
party member  党员
communist party of china n. 中国共产党
coronary[ˈkɒr-nə-ri] adj. 冠状  PS:这类病毒的形态看上去像中世纪欧洲帝王的皇冠，因此命名为“冠状病毒”。冠状病毒是一类主要引起呼吸道、肠道疾病的病原体。

###########################################################

```



## 00-开发者,初版发行时间; 有什么用,解决了什么痛点; 为什么偏偏选择你,而不是其他的类似的工具



> PS: 规定 统一用如下方式(即 万式计数方案 )进行数字表达,  例如  三万六千七百一十  => 3`6710
>
> PPS: 去踏马的 "千式计数", 老子早都不耐烦了 , 一帮煞笔外国佬 , 和中国国内部分追捧这种反文化和反惯性的舔狗们 , 特别是部分国家统计局的煞笔们 ,  沃柑雷们某!
>
> PPPS: 千式计数方案, 可以说很大程度上 是由于 2^10==1024 ~=1000  . 只要计算机的二进制基础不变, 这种千式计数方案就一直有存在的必要 , 特别是对于 "计算机专业 或 相关专业"的人们!  但是,尼玛的, 中国国内的搞税务统计的 搞文学的 搞编辑的 都尼玛用这种千式计数方案 , 贱不贱呢你们?  糙泥马! 舔狗去屎!
>
> 
>
> PPPS:
>
> > 1.English 的换行取决于空格(即 Space )和连字符(英文 Hypen, 形如"-")；
> >
> > 2.汉语随时都可以换行
>
> 
>
> PPPPS:文档结构符号约定 从左至右 优先级从高到低 e.g. 01- , 1#, 1>, (1), 1) ; 共5级





> 沃柑 or 沃橙 or 沃丢 or 沃草
>
> 糙泥马
>
> 莎比 or 沙笔 or 煞笔
>
> 雷某 or 雷门某
>
> 去蚀 or 去屎





### 1#开发者,初版发行时间

由Dan Abramov和Andrew Clark创建

初版发行于2015年

> Redux是由Facebook的Flux演变而来，并受到了函数式编程语言Elm的启发。 
> 截至2017年6月，Redux在Github上的Star数量为3`2250. 



---



Redux 是 PC-WebAPP 的 状态管理的开源 JavaScript库 。

它最常与React或Angular之类的库一起使用来构建用户界面 。 

Redux是一个小型库，具有简单，有限的API，旨在作为 PC-WebApp 的 可预测的状态容器。它允许你自由传输并处理 component 的state，允许父子关系与非父子关系的 component 之间传递 state 值。

> A Predictable State Container for JS Apps



### 2#有什么用,解决了什么痛点?

![å¨è¿éæå¥å¾çæè¿°](https://img-blog.csdnimg.cn/20190628114002819.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly96aGVuZ2thaS5ibG9nLmNzZG4ubmV0,size_16,color_FFFFFF,t_70) 

> blog.csdn.net/moshowgame/article/details/93979570

`没有使用Redux`的情况，如果`两个组件`之间需要通信的话，可能需要多个中间组件为他们进行消息传递，这样既浪费了资源，代码也会比较复杂。

 

### 3#为什么偏偏选择你,而不是其他的类似的工具

我们知道在一个 React 项目中，一般会定义许许多多的组件，每个组件都有自己的 `State`，通常情况下会通过 `setState` 去更改组件状态或者响应用户的在 UI 上的输入，但是随着一个 App 的内容的增加以及逻辑复杂度的上升，组件的的状态会变得越来越臃肿，继而变得难以维护（维护困难也是 React 最大的痛点）。所以，这个时候就该 Redux 出场了，我们通过引入它来帮助我们**管理组件的状态**。

简单来说，有了 Redux 之后，我们基本上就不需要自己去 `setState` 了，因为几乎所有的 State 的变化都可以交给 Redux 来管理。

> jianshu.com/p/6f95bf723301



---



React-Redux 是 Redux 官方推荐的框架



## 01-知识预热

> 就是几篇Blog而已, 当做爽文即可 , 不需要你动脑子 ... ...
>
> 是的 , 在这个环节暂时不需要你深入思考,但要求你仔细的仔细的仔细的去看文章!!!

### 1#Thanks AJIEW

> jianshu.com/p/6f95bf723301
>
> 鉴于React 和 ReactNative(简写为 RN) 二者之间的 特殊联系 , ***下文中的RN均可以等价理解为React***



#### 1>若干概念

Redux 中的这4个概念是需要我们掌握的，分别是 `Action`, `Reducer`, `Store`, `Dispatch`. 

项目中，一般会定义许许多多的组件，每个组件都有自己的 `State`，通常情况下会通过 `setState` 去更改组件状态或者响应用户的在 UI 上的输入，但是随着一个 App 的内容的增加以及逻辑复杂度的上升，组件的的状态会变得越来越臃肿，继而变得难以维护（维护困难也是 RN 最大的痛点）。

Redux可以帮助我们 管理 component 的 State. 简单来说，有了 Redux 之后，我们基本上就不需要自己去 `setState` 了，因为几乎所有 涉及 State 的操作 都可以交由 Redux 来执行。

 

---



需要改变 State 的 component 需要执行发出 Action 的 Dispatch (即 发送)操作 ，然后 Reducer 根据当前component所持有的State 并结合 刚刚传入的 Action 进行处理 ,最终返回一个new_state ( 即 新的State ) 给Store 。 

> State 保存在 Store 的 State-Tree 中



---

文字太枯燥，来看下面这张图辅助理解：



![img](https://upload-images.jianshu.io/upload_images/788577-40f753cadcc64ff0.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/480/format/webp) 



上图是一个非常经典的 "Redux Data Flow" 示意图

1st. React工程 的 component 绑定了 Redux 之后，component 就可以调用 `store.dispatch()` 去发射 action 了（比如基于 button 的点击事件 来发送 action）

2nd. store 接收到 action 之后，会把 "已有的 state"(我的理解是，每个component都具备初始状态的state值 ) 连同 action 二者作为参数  传递给 reducer ；然后 reducer 会根据开发者 所定义 的 逻辑流程 去处理 接受到的参数 ，然后返回  new_state 给 store 

3rd. store 会把  new_state 返回给 发射action的 component.  至此，UI完成了一次更新变幻。



---



Reducer 是如何更改 state 的 ？

```javascript
function textReducer(state = {}, action) {
  let text = action.text;
  let color = action.color;
  // 判断 action 类型
  switch (action.type) {
    case CHANGE_TEXT:
      // 返回新状态
      return Object.assign(
      	{}, 
            state, 
           {text: '新文字：' + text,
            color: color}
      );
    default:
      return state;
  }
}

//Object.assign() 冗长的写法会迅速降低 reducer 的可读性。一个可行的替代方案是使用最近加入 JavaScript 规范的 对象展开运算符。对象展开运算符让你可以通过展开运算符 (...) , 以更加简洁的形式将一个对象的可枚举属性拷贝至另一个对象。当你在组合复杂对象时, 使用对象展开运算符带来的好处将更加突出。
//我们试着用这种方式简化 textReducer

function textReducer(state = {}, action) {
  let text = action.text;
  let color = action.color;
  // 判断 action 类型
  switch (action.type) {
    case CHANGE_TEXT:
      // 返回新状态
      return {
        		...state, 
        		{text:'新文字'+text,color:color,}
             }
    default:
      return state;
  }
}

```

Redux语法规定，reducer 中不可以改变原来的 state，也就是要保持 `Object.assign()` 中的第一个参数为NULL，详见L9处代码。

> 不直接修改 state 亦是 Redux 的核心理念 



----



**问：**React工程的 component 是如何更新的？

**答：**当把所有的 state 都交给 Redux 之后，Redux 在 store 中就保存了PC-WebAPP所有的 state ，这意味着我们可以在任意位置获取到这些 state。
在 React 工程中，我们通过 React-Redux 来连接 Redux 和 component，然后在组件中通过将 state 映射成 props 来使用。也就是说，借助 `this.props.xxx` 就可以完成以下三种

>  数据的展示,
>
> 响应用户输入,
>
> UI 的变幻。

 

---

#### 2>API简介

了解了 Redux 基本概念之后就可以来学习一下如何使用了。

之前举了个 Action Creator 和 reducer 的例子，也知道了我们需要通过 store 来将这两者绑定在一起，但是 store 究竟还有哪些作用呢？store 主要有以下职责：

- 保存应用状态（state）
- 提供对 state 的访问：[getState()](https://links.jianshu.com/go?to=https%3A%2F%2Fredux.js.org%2Fapi%2Fstore%23getState) 
- 提供对状态进行更新的方法： [dispatch(action)](https://links.jianshu.com/go?to=https%3A%2F%2Fredux.js.org%2Fapi%2Fstore%23dispatch) 
- 注册监听器： [subscribe(listener)](https://links.jianshu.com/go?to=https%3A%2F%2Fredux.js.org%2Fapi%2Fstore%23subscribe) 
- 借助  [subscribe(listener)](https://links.jianshu.com/go?to=https%3A%2F%2Fredux.js.org%2Fapi%2Fstore%23subscribe) 的"return方法" 来理解 "注册监听器"

可以看出 store 就像**母体**一样，即保存了状态又连接了 Action Creator 和 reducer。但是究竟是怎么连接的呢？

*首先，之前说过我们的 reducer 可以定义 store 保存的 state 树结构，为什么呢？因为 reducer 是可以层层组合的。通常一个组件会有很多层级以及类型（比如 UI 和数据）的 state，我们不可能全都把他们定义在一个 reducer 里，这样代码会变得又长又难以维护。**正确的做法是我们应该把一个 reducer [拆分成多个 reducer](https://links.jianshu.com/go?to=https%3A%2F%2Fredux.js.org%2Fbasics%2Freducers%23splitting-reducers) 后再通过某种方式将它们组合起来。***



---



最常见的就是使用 [combineReducers()](https://links.jianshu.com/go?to=https%3A%2F%2Fredux.js.org%2Fapi%2Fcombinereducers) 方法来组合 reducer，它可以把多个 reducer 合并成一个 reducer 对象(下方所列代码中具体呈现为"伪reducer字典对象")，而合并后的 reducer 的层级结构就是我们访问 state 时的层级结构。
接收参数是 "伪reducer字典对象"，可以自己指定key，也可以直接组合，比如：

```ts
const allReducers = combineReducers(
  {  //伪字典对象
    textReducer,  // "直接组合",也就是仅指定"key"
    imageReducer,  //"直接组合",也就是仅指定"key"
    videoRed: videoReducer, //"指定key-value"
  });
```





> 对combineReducers()函数的更多介绍
> 节选自redux.js.org/api/combinereducers

As your app grows more complex, you'll want to split your [reducing function](https://redux.js.org/glossary#reducer) into separate functions, each managing independent parts of the [state](https://redux.js.org/glossary#state).

The `combineReducers` helper function turns an object whose values are different reducing functions into a single reducing function which you can pass to [`createStore`](https://redux.js.org/api/createstore).

The resulting reducer calls every child reducer, and gathers their results into a single state object. **The state produced by combineReducers() namespaces the states of each reducer under their keys as passed to combineReducers()**

Example:

```js
rootReducer = combineReducers({potato: potatoReducer, tomato: tomatoReducer})
// This would produce the following state object
{
  potato: {
    // ... potatoes, and other state managed by the potatoReducer ...
  },
  tomato: {
    // ... tomatoes, and other state managed by the tomatoReducer, maybe some nice sauce? ...
  }
}
```

You can control state key names by using different keys for the reducers in the passed object. For example, you may call `combineReducers({ todos: myTodosReducer, counter: myCounterReducer })` for the state shape to be `{ todos, counter }`. PS：也就是前文所述的"伪reducer字典对象" .

A popular convention is to name reducers after the state slices they manage, so you can use ES6 property shorthand notation: `combineReducers({ counter, todos })`. This is equivalent to writing `combineReducers({ counter: counter, todos: todos })`.

> 译文：一种流行的不成文约定是在reducer所管理的 state-slices 后命名，也就是说您可以使用ES6属性的简写形式：
>
> ```json
> combinedReducers（{counter，todos}） 
> //这等效于编写
> CombineReducers（{counter：counter，todos：todos}）。
> ```



---



当把多个 reducer 合并成一个之后，我们就可以通过 [createStore](https://links.jianshu.com/go?to=https%3A%2F%2Fredux.js.org%2Fapi%2Fcreatestore) 来创建 store 了，它唯一必须的参数是 reducer，也就是 `combineReducers(reducers)` 所返回的 reducer。

第二个参数是可选的初始状态 `preloadedState`。我们可以从服务器读取初始状态，或者在 app 启动时从本地数据读取初始状态。

第三个参数也是可选的 `enhancer`，接收的是一个函数，可以是你想要提供的第三方的功能，比如 Redux 自带的 applyMiddleware()

```ts
const allReducers = combineReducers({textReducer});

let store = createStore(allReducers, applyMiddleware(thunkMiddleware));
//createStore() 返回的 store 就是保存了应用全局 state 的对象了，这个时候我们就可以使用 getState() 并且根据 reducer 的层级来访问保存在其中的 state 了！

export default store;
```

 

### 2#Thanks GIANTS

> juejin.im/post/5bac26ad6fb9a05d353c8040

#### 1>若干概念

***Redux特性 简介如下***


单一数据源： 整个应用的 state 被储存在一棵 object tree 中，并且这个 object tree 只存在于唯一的sto-re中。


State 是只读的：唯一改变 state 的方法就是触发 action，action 是一个用于描述已发生事件的普通对象。


使用纯函数来执行修改：为了描述 action 如何改变 state tree ，你需要编写 reducers。


预见性：所有的用户的行为都是你提前编写好的。


统一管理state：所有的状态都在且只在一个store中分配管理。



---



redux能帮我们做什么

两张图示意：

![未使用redux的大型react native项目](https://user-gold-cdn.xitu.io/2018/10/11/16662dcc4183aadb?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

![使用redux后的大型react native项目](https://user-gold-cdn.xitu.io/2018/10/11/16662dcc38809357?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)



---



哪些开发者和项目适合用redux

这里只针对`react native`开发而言：

- 初级：刚接触`react native`我非常不建议去使用，因为你还不知道怎么用它，建议先达到中级。

- 中级：使用`react native`做出一个以上已经上架的`不复杂`的应用 `redux`，也可以不使用，因为使用它并不能让你在前期快速的迭代开发，在这样的项目下使用`redux`就好比`大炮打蚊子`，副作用很大。但是可以先了解起来，并发现它的优点。这类相对简单的应用：当用户触发一个动作（程序需要`setState({xxx:xxx})`)的时候应用程序状态流程是这样的： 

  ![简单的状态流程](https://user-gold-cdn.xitu.io/2018/10/11/16662dcc41777f00?imageslim)

  

- 高级：使用`react native`做出一个以上已经上架的`复杂`的应用(涉及到即时通讯、界面布局比较复杂，组件嵌套太多层次等)，而这类复杂应用：当用户触发一个动作（程序需要`setState({xxx:xxx})`)的时候应用程序状态流程是这样的： 

  ![复杂的状态流程](https://user-gold-cdn.xitu.io/2018/10/11/16662dcc7a3e1acf?imageslim)

  

这种状态带来的后果，两方面分析：

- 性能：祖父子组件之间多余的状态传递，导致宝贵的内存资源浪费，同时界面渲染的速度也会变慢，自然用户体验就变差了。
- 状态管理：当程序不断的迭代，界面布局越来越复杂，必然就会产生许多的`state`状态，那你是如何有效的管理这些状态？是什么原因导致UI多次渲染？是哪一步操作导致的UI组件的变化？在没有使用`redux`前你可能已经发现可以使用生命周期函数中的`shouldComponentUpdate`来减少子组件中没必要的渲染，但终究解决不了状态管理复杂的难题。 当你使用`redux`后，复杂的应用程序状态流程是这样的：

 

 ![使用redux后](https://user-gold-cdn.xitu.io/2018/10/11/16662dcc7a2251ec?imageslim)

 

---



redux for react native 工作逻辑图

感谢@[黑森林工作室](https://www.jianshu.com/u/8b645668c3c4)作者提供的清晰的逻辑图

![清晰逻辑图](https://user-gold-cdn.xitu.io/2018/10/11/16662dcc71fab472?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)



PS：注意比较其他的几张图，对初学的自学者而言 持怀疑谨慎的态度总归是好的。。。



---



需要注意的事

- 一个工程中 `redux` 的 `store` 是唯一的，不能在多个 `store`  。

- 保持 `reducer` 纯净非常重要。永远不要在 `reducer` 里做这些操作：

  > ***永远不要*** 在 `reducer` 里做这些操作:
  >
  > ​	修改传入参数；
  >
  > ​	执行有副作用的操作，如 `API` 请求和路由跳转；
  >
  > ​	调用非纯函数，如 `Date.now()` 或 `Math.random()`;



- 使用 "对象展开运算符"`...`代替`Object.assign()` 无疑是更好的编码习惯

  > 对象展开运算符（Object Spread Operator）简介：
  >
  > 它让你以更加简洁的形式将一个对象的可枚举属性拷贝至另一个对象。对象展开运算符在概念上与 ES6 的 [数组展开运算符](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator) 相似。
  > 另参考  cn.redux.js.org/docs/recipes/UsingObjectSpreadOperator.html

- 组件名首字母要大写，也就是说`components`和`containers`文件夹下的文件首字母都要大写。

- 应该尽量减少传递到`action` 中的数据（能传单个数据就不传对象，能传对象就不传数组）

 

---



Middleware（中间固件）的作用

> The main difference between **firmware** and **middleware** is that the **firmware** is a type of software that allows controlling the device's hardware while the **middleware** is a software that provides services to software applications beyond those available from the operating system. 
>
> 参考网址 ：pediaa.com/difference-between-firmware-and-middleware/



`Middleware`是在`Actions`和`Dispatcher`之间被嵌入的为了解决某些问题、提高我们开发效率而存在的工具。 下面介绍三种常用的中间件：

- [redux-thunk](https://github.com/reduxjs/redux-thunk) 中间件：项目中的异步操作需要用到（例如：请求服务器数据、本地存储等）。
- [redux-actions](https://github.com/redux-utilities/redux-actions) 中间件：帮助处理和创建操作`actions`（本文不做介绍，后续项目复杂后可以使用它来创建）。
- [redux-logger](https://github.com/evgenyrodionov/redux-logger) 中间件：用来打印 `action` 日志。 开启`react native`远程调试模式，操作demo就能在控制台看到打印的状态前后变化。



加入中间件后的示意图如下：

![加入中间件后的示意图](https://user-gold-cdn.xitu.io/2018/10/11/16662dccc537af99?imageslim)

 

 

 

 

#### 2>Api 简介

> 略！！！



### 3#Thanks MOSHOW

> blog.csdn.net/moshowgame/article/details/93979570



# 待续



### 4#Thanks MDX

> juejin.im/post/5cc1ace96fb9a0321728245e

 

 

 

## 02-核心概念 Core Concepts 







## 03-工程上手+知识深入







## 04-待补充