# 第 1 章 权衡的艺术

## 1.1 命名式和声明式

如 JQ 一样的命令式编程，描述的是做事的过程

```js
$('#app') // 获取 div
  .text('hello world') // 设置文本内容
  .on('click', () => {
    alert('ok')
  }) // 绑定点击事件
```

如 Vue 一样的声明式编程（用了虚拟 DOM），更加关注结果，声明式编程的内部一定是命令式的，它封装了过程，暴露给用户的是结果

```vue
<div @click="() => alert('ok')">hello world</div>
```

## 1.2 性能和可维护性到权衡

`声明式代码更新性能消耗 = 找出差异的性能消耗 + 直接修改的性能消耗`

Vue 的理念是：**在保持可维护性的同时让性能损失最小化**

## 1.3 虚拟 DOM 的性能到底如何

因为上面说到的性能消耗一部分是`直接修改的性能消耗`这一步没办法做优化，而`找出差异的性能消耗`降到最低就是 Vue 要做的事情，也就是虚拟 DOM

1. 虚拟 DOM 理论上没有原生 JS 性能好，但是很难写出绝对优化的命令式代码，尤其是大型应用的时候。
2. 虚拟 DOM 在更新的时候，只需要 diff 找到需要更新的位置更新对应元素，所以`虚拟 DOM 保证了性能的下限`，`增加了可维护性`，`减少了心智负担`。

## 1.4 运行时和编译时

Vue 是运行时加编译时的框架

纯运行时无法分析用户提供的内容，纯编译时如 svelte 也就是只有 render 灵活性没那么好，而运行时加编译时`compiler`和`render`

## 2.1 提升用户的开发体验

## 2.2 控制框架代码的体积

## 2.3 框架要做到良好的 tree-shaking

## 2.4 框架应该输出怎样的构建产物

## 2.5 特性开关

## 2.6 错误处理

## 2.7 良好的 Typescript 类型支持