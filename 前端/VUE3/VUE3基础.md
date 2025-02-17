# VUE3基础

# 简介

## 单文件组件

在大多数启用了构建工具的 Vue 项目中，我们可以使用一种类似 HTML 格式的文件来书写 Vue 组件，它被称为**单文件组件** (也被称为 `*.vue`​ 文件，英文 Single-File Components，缩写为 **SFC**)。顾名思义，Vue 的单文件组件会将一个组件的逻辑 (JavaScript)，模板 (HTML) 和样式 (CSS) 封装在同一个文件里。

## API 风格

### 选项式 API

使用选项式 API，我们可以用包含多个选项的对象来描述组件的逻辑，例如 `data`​、`methods`​ 和 `mounted`​。选项所定义的属性都会暴露在函数内部的 `this`​ 上，它会指向当前的组件实例。

```javascript
<script>
export default {
  // data() 返回的属性将会成为响应式的状态
  // 并且暴露在 `this` 上
  data() {
    return {
      count: 0
    }
  },

  // methods 是一些用来更改状态与触发更新的函数
  // 它们可以在模板中作为事件处理器绑定
  methods: {
    increment() {
      this.count++
    }
  },

  // 生命周期钩子会在组件生命周期的各个不同阶段被调用
  // 例如这个函数就会在组件挂载完成后被调用
  mounted() {
    console.log(`The initial count is ${this.count}.`)
  }
}
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>
```

### 组合式 API

通过组合式 API，我们可以使用导入的 API 函数来描述组件逻辑。在单文件组件中，组合式 API 通常会与 [`&lt;script setup&gt;`](https://cn.vuejs.org/api/sfc-script-setup.html)​ 搭配使用。这个 `setup`​ attribute 是一个标识，告诉 Vue 需要在编译时进行一些处理，让我们可以更简洁地使用组合式 API。比如，`<script setup>`​ 中的导入和顶层变量/函数都能够在模板中直接使用。

```javascript
<script setup>
import { ref, onMounted } from 'vue'

// 响应式状态
const count = ref(0)

// 用来修改状态、触发更新的函数
function increment() {
  count.value++
}

// 生命周期钩子
onMounted(() => {
  console.log(`The initial count is ${count.value}.`)
})
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>
```

# 创建应用

## 安装

在本节中，我们将介绍如何在本地搭建 Vue [单页应用](https://cn.vuejs.org/guide/extras/ways-of-using-vue.html#single-page-application-spa)。创建的项目将使用基于 [Vite](https://vitejs.dev/) 的构建设置，并允许我们使用 Vue 的[单文件组件](https://cn.vuejs.org/guide/scaling-up/sfc.html) (SFC)。

确保你安装了最新版本的 [Node.js](https://nodejs.org/)，并且你的当前工作目录正是打算创建项目的目录。在命令行中运行以下命令 (不要带上 `$`​ 符号)：

```shell
npm create vue@latest
```

这一指令将会安装并执行 [create-vue](https://github.com/vuejs/create-vue)，它是 Vue 官方的项目脚手架工具。你将会看到一些诸如 TypeScript 和测试支持之类的可选功能提示

如果不确定是否要开启某个功能，你可以直接按下回车键选择 `No`​

## 启动

在项目被创建后，通过以下步骤安装依赖并启动开发服务器

```shell
cd <your-project-name>
npm install
npm run dev
```

当你准备将应用发布到生产环境时，请运行

```shell
npm run build
```

此命令会在 `./dist`​ 文件夹中为你的应用创建一个生产环境的构建版本。关于将应用上线生产环境的更多内容，请阅读[生产环境部署指南](https://cn.vuejs.org/guide/best-practices/production-deployment.html)。

## 应用实例

每个 Vue 应用都是通过 [`createApp`](https://cn.vuejs.org/api/application.html#createapp)​ 函数创建一个新的 **应用实例**

```JavaScript
// main.ts
import { createApp } from 'vue'

const app = createApp({
  /* 根组件选项 */
})
```

## 根组件

我们传入 `createApp`​ 的对象实际上是一个组件，每个应用都需要一个“根组件”，其他组件将作为其子组件。

如果你使用的是单文件组件，我们可以直接从另一个文件中导入根组件。

```JavaScript
// main.ts
import { createApp } from 'vue'
// 从一个单文件组件中导入根组件
import App from './App.vue'

const app = createApp(App)
```

## 挂载应用

应用实例必须在调用了 `.mount()`​ 方法后才会渲染出来。该方法接收一个“容器”参数，可以是一个实际的 DOM 元素或是一个 CSS 选择器字符串：

```HTML
<div id="app"></div>
```

```javascript
app.mount('#app')
```

应用根组件的内容将会被渲染在容器元素里面。容器元素自己将**不会**被视为应用的一部分。

​`.mount()`​ 方法应该始终在整个应用配置和资源注册完成后被调用。同时请注意，不同于其他资源注册方法，它的返回值是根组件实例而非应用实例。

## 应用配置

应用实例会暴露一个 `.config`​ 对象允许我们配置一些应用级的选项，例如定义一个应用级的错误处理器，用来捕获所有子组件上的错误

```javascript
app.config.errorHandler = (err) => {
  /* 处理错误 */
}
```

应用实例还提供了一些方法来注册应用范围内可用的资源，例如注册一个组件：

```javascript
app.component('TodoDeleteButton', TodoDeleteButton)
```

这使得 `TodoDeleteButton`​ 在应用的任何地方都是可用的。我们会在指南的后续章节中讨论关于组件和其他资源的注册。你也可以在 [API 参考](https://cn.vuejs.org/api/application.html)中浏览应用实例 API 的完整列表。

确保在挂载应用实例之前完成所有应用配置！

## 多个应用实例

应用实例并不只限于一个。`createApp`​ API 允许你在同一个页面中创建多个共存的 Vue 应用，而且每个应用都拥有自己的用于配置和全局资源的作用域。

```javascript
// main.ts
const app1 = createApp({
  /* ... */
})
app1.mount('#container-1')

const app2 = createApp({
  /* ... */
})
app2.mount('#container-2')
```

如果你正在使用 Vue 来增强服务端渲染 HTML，并且只想要 Vue 去控制一个大型页面中特殊的一小部分，应避免将一个单独的 Vue 应用实例挂载到整个页面上，而是应该创建多个小的应用实例，将它们分别挂载到所需的元素上去。

# 模板语法

Vue 使用一种基于 HTML 的模板语法，使我们能够声明式地将其组件实例的数据绑定到呈现的 DOM 上。所有的 Vue 模板都是语法层面合法的 HTML，可以被符合规范的浏览器和 HTML 解析器解析。

在底层机制中，Vue 会将模板编译成高度优化的 JavaScript 代码。结合响应式系统，当应用状态变更时，Vue 能够智能地推导出需要重新渲染的组件的最少数量，并应用最少的 DOM 操作。

## 文本插值

最基本的数据绑定形式是文本插值，它使用的是“Mustache”语法 (即双大括号)：

```html
<span>Message: {{ msg }}</span>
```

双大括号标签会被替换为[相应组件实例中](https://cn.vuejs.org/guide/essentials/reactivity-fundamentals.html#declaring-reactive-state) `msg`​ 属性的值。同时每次 `msg`​ 属性更改时它也会同步更新。

## 原始HTML

双大括号会将数据解释为纯文本，而不是 HTML。若想插入 HTML，你需要使用 [`v-html`](https://cn.vuejs.org/api/built-in-directives.html#v-html)​[ 指令](https://cn.vuejs.org/api/built-in-directives.html#v-html)

```html
<p>Using text interpolation: {{ rawHtml }}</p>
<p>Using v-html directive: <span v-html="rawHtml"></span></p>
```

这里看到的 `v-html`​ attribute 被称为一个**指令**。指令由 `v-`​ 作为前缀，表明它们是一些由 Vue 提供的特殊 attribute，你可能已经猜到了，它们将为渲染的 DOM 应用特殊的响应式行为。这里我们做的事情简单来说就是：在当前组件实例上，将此元素的 innerHTML 与 `rawHtml`​ 属性保持同步。

​`span`​ 的内容将会被替换为 `rawHtml`​ 属性的值，插值为纯 HTML——数据绑定将会被忽略。注意，你不能使用 `v-html`​ 来拼接组合模板，因为 Vue 不是一个基于字符串的模板引擎。在使用 Vue 时，应当使用组件作为 UI 重用和组合的基本单元。

## Attribute 绑定

双大括号不能在 HTML attributes 中使用。想要响应式地绑定一个 attribute，应该使用 [`v-bind`](https://cn.vuejs.org/api/built-in-directives.html#v-bind)​[ 指令](https://cn.vuejs.org/api/built-in-directives.html#v-bind)

```html
<div v-bind:id="dynamicId"></div>
```

​`v-bind`​ 指令指示 Vue 将元素的 `id`​ attribute 与组件的 `dynamicId`​ 属性保持一致。如果绑定的值是 `null`​ 或者 `undefined`​，那么该 attribute 将会从渲染的元素上移除。

### 简写

因为 `v-bind`​ 非常常用，我们提供了特定的简写语法：

```html
<div :id="dynamicId"></div>
```

开头为 `:`​ 的 attribute 可能和一般的 HTML attribute 看起来不太一样，但它的确是合法的 attribute 名称字符，并且所有支持 Vue 的浏览器都能正确解析它。此外，他们不会出现在最终渲染的 DOM 中。

### 同名简写

* 仅支持 3.4 版本及以上

如果 attribute 的名称与绑定的 JavaScript 值的名称相同，那么可以进一步简化语法，省略 attribute 值：

```html
<!-- 与 :id="id" 相同 -->
<div :id></div>

<!-- 这也同样有效 -->
<div v-bind:id></div>
```

这与在 JavaScript 中声明对象时使用的属性简写语法类似。请注意，这是一个只在 Vue 3.4 及以上版本中可用的特性。

### 布尔型 Attribute

[布尔型 attribute](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Attributes#%E5%B8%83%E5%B0%94%E5%80%BC%E5%B1%9E%E6%80%A7) 依据 true / false 值来决定 attribute 是否应该存在于该元素上。[`disabled`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/disabled)​ 就是最常见的例子之一。

​`v-bind`​ 在这种场景下的行为略有不同：

```html
<button :disabled="isButtonDisabled">Button</button>
```

当 `isButtonDisabled`​ 为[真值](https://developer.mozilla.org/en-US/docs/Glossary/Truthy)或一个空字符串 (即 `<button disabled="">`​) 时，元素会包含这个 `disabled`​ attribute。而当其为其他[假值](https://developer.mozilla.org/en-US/docs/Glossary/Falsy)时 attribute 将被忽略。

### 动态绑定多个值

如果你有像这样的一个包含多个 attribute 的 JavaScript 对象：

```javascript
const objectOfAttrs = {
  id: 'container',
  class: 'wrapper',
  style: 'background-color:green'
}
```

通过不带参数的 `v-bind`​，你可以将它们绑定到单个元素上：

```html
<div v-bind="objectOfAttrs"></div>
```

## 使用JavaScript表达式

Vue 实际上在所有的数据绑定中都支持完整的 JavaScript 表达式

```html
{{ number + 1 }}

{{ ok ? 'YES' : 'NO' }}

{{ message.split('').reverse().join('') }}

<div :id="`list-${id}`"></div>
```

在 Vue 模板内，JavaScript 表达式可以被使用在如下场景上：

* 在文本插值中 (双大括号)
* 在任何 Vue 指令 (以 `v-`​ 开头的特殊 attribute) attribute 的值中

### 仅支持表达式

每个绑定仅支持**单一表达式**，也就是一段能够被求值的 JavaScript 代码。一个简单的判断方法是是否可以合法地写在 `return`​ 后面。

因此，下面的例子都是**无效**的：

```html
<!-- 这是一个语句，而非表达式 -->
{{ var a = 1 }}

<!-- 条件控制也不支持，请使用三元表达式 -->
{{ if (ok) { return message } }}
```

### 调用函数

可以在绑定的表达式中使用一个组件暴露的方法：

```html
<time :title="toTitleDate(date)" :datetime="date">
  {{ formatDate(date) }}
</time>
```

TIP：绑定在表达式中的方法在组件每次更新时都会被重新调用，因此**不**应该产生任何副作用，比如改变数据或触发异步操作。

### 受限的全局访问

模板中的表达式将被沙盒化，仅能够访问到[有限的全局对象列表](https://github.com/vuejs/core/blob/main/packages/shared/src/globalsAllowList.ts#L3)。该列表中会暴露常用的内置全局对象，比如 `Math`​ 和 `Date`​。

没有显式包含在列表中的全局对象将不能在模板内表达式中访问，例如用户附加在 `window`​ 上的属性。然而，你也可以自行在 [`app.config.globalProperties`](https://cn.vuejs.org/api/application.html#app-config-globalproperties)​ 上显式地添加它们，供所有的 Vue 表达式使用。

## 指令

指令是带有 `v-`​ 前缀的特殊 attribute。Vue 提供了许多[内置指令](https://cn.vuejs.org/api/built-in-directives.html)，包括上面我们所介绍的 `v-bind`​ 和 `v-html`​。

指令 attribute 的期望值为一个 JavaScript 表达式 (除了少数几个例外，即之后要讨论到的 `v-for`​、`v-on`​ 和 `v-slot`​)。一个指令的任务是在其表达式的值变化时响应式地更新 DOM。

```html
<p v-if="seen">Now you see me</p>
```

这里，`v-if`​ 指令会基于表达式 `seen`​ 的值的真假来移除/插入该 `<p>`​ 元素。

### 参数 Arguments

某些指令会需要一个“参数”，在指令名后通过一个冒号隔开做标识。例如用 `v-bind`​ 指令来响应式地更新一个 HTML attribute：

```html
<a v-bind:href="url"> ... </a>

<!-- 简写 -->
<a :href="url"> ... </a>
```

另一个例子是 `v-on`​ 指令，它将监听 DOM 事件：

```html
<a v-on:click="doSomething"> ... </a>

<!-- 简写 -->
<a @click="doSomething"> ... </a>
```

这里的参数是要监听的事件名称：`click`​。`v-on`​ 有一个相应的缩写，即 `@`​ 字符。

### 动态参数

同样在指令参数上也可以使用一个 JavaScript 表达式，需要包含在一对方括号内：

```html
<!--
注意，参数表达式有一些约束，
参见下面“动态参数值的限制”与“动态参数语法的限制”章节的解释
-->
<a v-bind:[attributeName]="url"> ... </a>

<!-- 简写 -->
<a :[attributeName]="url"> ... </a>
```

这里的 `attributeName`​ 会作为一个 JavaScript 表达式被动态执行，计算得到的值会被用作最终的参数。举例来说，如果你的组件实例有一个数据属性 `attributeName`​，其值为 `"href"`​，那么这个绑定就等价于 `v-bind:href`​。

相似地，你还可以将一个函数绑定到动态的事件名称上：

```html
<a v-on:[eventName]="doSomething"> ... </a>

<!-- 简写 -->
<a @[eventName]="doSomething"> ... </a>
```
