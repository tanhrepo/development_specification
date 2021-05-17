# Vue文件命名





## 组件名为多个单词

**组件名应该始终是多个单词的，根组件 `App` 以及 `<transition>`、`<component>` 之类的 Vue 内置组件除外。**

这样做可以避免跟现有的以及未来的 HTML 元素[相冲突](http://w3c.github.io/webcomponents/spec/custom/#valid-custom-element-name)，因为所有的 HTML 元素名称都是单个单词的。

#### 反例

```js
app.component('todo', {
  // ...
})
```

```js
export default {
  name: 'Todo',
  // ...
}
```

#### 好例子

```js
app.component('todo-item', {
  // ...
})
```

```js
export default {
  name: 'TodoItem',
  // ...
}
```

## 文件夹命名规范

#### 属于`components`文件夹下的子文件夹，使用大写字母开头的`PascalBase`风格

1. 全局通用的组件放在 /src/components下
2. 其他业务页面中的组件，放在各自页面下的 ./components文件夹下
3. 每个components文件夹下最多只有一层文件夹，且文件夹名称为组件的名称，文件夹下必须有`index.vue`或
   `index.js`，其他.vue文件统一大写开头（Pascal case），`components`下的子文件夹名称统一大写开头（PascalCase）

#### 其他文件夹统一使用`kebab-case`的风格







## 单文件组件文件的大小写

**`单文件组件`的文件名应该始终是单词大写开头 (PascalCase)**

单词大写开头对于代码编辑器的自动补全最为友好，因为这使得我们在 JS(X) 和模板中引用组件的方式尽可能的一致。

#### 反例

```
components/
|- mycomponent.vue		//官方不推荐
components/
|- myComponent.vue		//官方不推荐
components/
|- my-component.vue		//官方推荐，团队不推荐
```

#### 好例子

```
components/
|- MyComponent.vue		//官方推荐，团队推荐
```



## 基础组件名

**应用特定样式和约定的基础组件 (也就是展示类的、无逻辑的或无状态的组件) 应该全部以一个特定的前缀开头，比如 `Base`、`App` 或 `V`。**

<details open="" style="border-radius: 2px; margin: 1.6em 0px; padding: 1.6em; background-color: rgb(238, 238, 238); display: block; position: relative; color: rgb(48, 68, 85); font-family: &quot;Source Sans Pro&quot;, &quot;Helvetica Neue&quot;, Arial, sans-serif; font-size: 16px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary style="cursor: pointer; padding: 1.6em; margin: -1.6em; outline: none;"><h4 style="font-weight: 600; color: rgb(39, 56, 73); margin: 0px; display: inline-block;">详解</h4></summary><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: relative; z-index: 1;">这些组件为你的应用奠定了一致的基础样式和行为。它们可能<strong style="font-weight: 600; color: rgb(39, 56, 73);">只</strong>包括：</p><ul style="line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: inherit; z-index: 1; padding-left: 1.5em;"><li>HTML 元素</li><li>其它基础组件</li><li>第三方 UI 组件库</li></ul><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: relative; z-index: 1;">但是它们<strong style="font-weight: 600; color: rgb(39, 56, 73);">绝不会</strong>包括全局状态 (比如来自 Vuex store)。</p><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: relative; z-index: 1;">它们的名字通常包含所包裹元素的名字 (比如<span>&nbsp;</span><code style="font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85em; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial; color: rgb(214, 50, 0); padding: 3px 5px; margin: 0px 2px; border-radius: 2px; white-space: nowrap;">BaseButton</code>、<code style="font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85em; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial; color: rgb(214, 50, 0); padding: 3px 5px; margin: 0px 2px; border-radius: 2px; white-space: nowrap;">BaseTable</code>)，除非没有现成的对应功能的元素 (比如<span>&nbsp;</span><code style="font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85em; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial; color: rgb(214, 50, 0); padding: 3px 5px; margin: 0px 2px; border-radius: 2px; white-space: nowrap;">BaseIcon</code>)。如果你为特定的上下文构建类似的组件，那它们几乎总会消费这些组件 (比如<span>&nbsp;</span><code style="font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85em; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial; color: rgb(214, 50, 0); padding: 3px 5px; margin: 0px 2px; border-radius: 2px; white-space: nowrap;">BaseButton</code><span>&nbsp;</span>可能会用在<span>&nbsp;</span><code style="font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85em; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial; color: rgb(214, 50, 0); padding: 3px 5px; margin: 0px 2px; border-radius: 2px; white-space: nowrap;">ButtonSubmit</code><span>&nbsp;</span>上)。</p><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: relative; z-index: 1;">这样做的几个好处：</p><ul style="line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: inherit; z-index: 1; padding-left: 1.5em;"><li><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px 0px; padding-bottom: 0px; position: relative; z-index: 1;">当你在编辑器中以字母顺序排序时，你的应用的基础组件会全部列在一起，这样更容易识别。</p></li><li><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px 0px; padding-bottom: 0px; position: relative; z-index: 1;">因为组件名应该始终是多个单词，所以这样做可以避免你在包裹简单组件时随意选择前缀 (比如<span>&nbsp;</span><code style="font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85em; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial; color: rgb(214, 50, 0); padding: 3px 5px; margin: 0px 2px; border-radius: 2px; white-space: nowrap;">MyButton</code>、<code style="font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85em; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial; color: rgb(214, 50, 0); padding: 3px 5px; margin: 0px 2px; border-radius: 2px; white-space: nowrap;">VueButton</code>)。</p></li><li><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: relative; z-index: 1;">因为这些组件会被频繁使用，所以你可能想把它们放到全局而不是在各处分别导入它们。使用相同的前缀可以让 webpack 这样工作：</p><pre style="border-radius: 2px; position: relative; font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85em; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial;"><code class="hljs js" style="font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85rem; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial; color: rgb(82, 82, 82); padding: 1.2em 1.4em; margin: 0px 2px; border-radius: 2px; white-space: pre; overflow-x: auto; line-height: 1.6rem; display: block;"><span class="hljs-keyword" style="color: rgb(214, 50, 0);">var</span> requireComponent = <span class="hljs-built_in" style="color: rgb(66, 185, 131);">require</span>.context(<span class="hljs-string" style="color: rgb(66, 185, 131);">"./src"</span>, <span class="hljs-literal" style="color: rgb(163, 46, 255);">true</span>, /Base[A-Z]\w+\.(vue|js)$/)
requireComponent.keys().forEach(<span class="hljs-function"><span class="hljs-keyword" style="color: rgb(214, 50, 0);">function</span> (<span class="hljs-params">fileName</span>) </span>{
  <span class="hljs-keyword" style="color: rgb(214, 50, 0);">var</span> baseComponentConfig = requireComponent(fileName)
  baseComponentConfig = baseComponentConfig.default || baseComponentConfig
  <span class="hljs-keyword" style="color: rgb(214, 50, 0);">var</span> baseComponentName = baseComponentConfig.name || (
    fileName
      .replace(<span class="hljs-regexp" style="color: rgb(66, 185, 131);">/^.+\//</span>, <span class="hljs-string" style="color: rgb(66, 185, 131);">''</span>)
      .replace(<span class="hljs-regexp" style="color: rgb(66, 185, 131);">/\.\w+$/</span>, <span class="hljs-string" style="color: rgb(66, 185, 131);">''</span>)
  )
  Vue.component(baseComponentName, baseComponentConfig)
})</code></pre></li></ul></details>

#### 反例

```
components/
|- MyButton.vue
|- VueTable.vue
|- Icon.vue
```

#### 好例子

```
components/
|- BaseButton.vue
|- BaseTable.vue
|- BaseIcon.vue
components/
|- AppButton.vue
|- AppTable.vue
|- AppIcon.vue
components/
|- VButton.vue
|- VTable.vue
|- VIcon.vue
```





## 单例组件名

**只应该拥有单个活跃实例的组件应该以 `The` 前缀命名，以示其唯一性。**

这不意味着组件只可用于一个单页面，而是*每个页面*只使用一次。这些组件永远不接受任何 prop，因为它们是为你的应用定制的，而不是它们在你的应用中的上下文。如果你发现有必要添加 prop，那就表明这实际上是一个可复用的组件，*只是目前*在每个页面里只使用一次。

#### 反例

```
components/
|- Heading.vue
|- MySidebar.vue
```

#### 好例子

```
components/
|- TheHeading.vue
|- TheSidebar.vue
```



## 紧密耦合的组件名

**和父组件紧密耦合的子组件应该以父组件名作为`前缀`命名。**

如果一个组件只在某个父组件的场景下有意义，这层关系应该体现在其名字上。因为编辑器通常会按字母顺序组织文件，所以这样做可以把相关联的文件排在一起。

<details open="" style="border-radius: 2px; margin: 1.6em 0px; padding: 1.6em; background-color: rgb(238, 238, 238); display: block; position: relative; color: rgb(48, 68, 85); font-family: &quot;Source Sans Pro&quot;, &quot;Helvetica Neue&quot;, Arial, sans-serif; font-size: 16px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary style="cursor: pointer; padding: 1.6em; margin: -1.6em; outline: none;"><h4 style="font-weight: 600; color: rgb(39, 56, 73); margin: 0px; display: inline-block;">详解</h4></summary><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: relative; z-index: 1;">你可以试着通过在其父组件命名的目录中嵌套子组件以解决这个问题。比如：</p><pre style="border-radius: 2px; position: relative; font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85em; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial;"><code class="hljs undefined" style="font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85rem; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial; color: rgb(82, 82, 82); padding: 1.2em 1.4em; margin: 0px 2px; border-radius: 2px; white-space: pre; overflow-x: auto; line-height: 1.6rem; display: block;">components/
|- TodoList/
   |- Item/
      |- index.vue
      |- Button.vue
   |- index.vue</code></pre><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: relative; z-index: 1;">或：</p><pre style="border-radius: 2px; position: relative; font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85em; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial;"><code class="hljs undefined" style="font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85rem; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial; color: rgb(82, 82, 82); padding: 1.2em 1.4em; margin: 0px 2px; border-radius: 2px; white-space: pre; overflow-x: auto; line-height: 1.6rem; display: block;">components/
|- TodoList/
   |- Item/
      |- Button.vue
   |- Item.vue
|- TodoList.vue</code></pre><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: relative; z-index: 1;">但是这种方式并不推荐，因为这会导致：</p><ul style="line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: inherit; z-index: 1; padding-left: 1.5em;"><li>许多文件的名字相同，使得在编辑器中快速切换文件变得困难。</li><li>过多嵌套的子目录增加了在编辑器侧边栏中浏览组件所花的时间。</li></ul></details>

#### 反例

```
components/
|- TodoList.vue
|- TodoItem.vue
|- TodoButton.vue
components/
|- SearchSidebar.vue
|- NavigationForSearchSidebar.vue
```

#### 好例子

```
components/
|- TodoList.vue
|- TodoListItem.vue
|- TodoListItemButton.vue
components/
|- SearchSidebar.vue
|- SearchSidebarNavigation.vue
```





## 组件名中的单词顺序

**组件名应该以高级别的 (通常是一般化描述的) 单词开头，以描述性的修饰词结尾。**

<details open="" style="border-radius: 2px; margin: 1.6em 0px; padding: 1.6em; background-color: rgb(238, 238, 238); display: block; position: relative; color: rgb(48, 68, 85); font-family: &quot;Source Sans Pro&quot;, &quot;Helvetica Neue&quot;, Arial, sans-serif; font-size: 16px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary style="cursor: pointer; padding: 1.6em; margin: -1.6em; outline: none;"><h4 style="font-weight: 600; color: rgb(39, 56, 73); margin: 0px; display: inline-block;">详解</h4></summary><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: relative; z-index: 1;">你可能会疑惑：</p><blockquote style="margin: 2em 0px; padding-left: 20px; border-left: 4px solid rgb(66, 185, 131);"><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px 0px; padding-bottom: 0px; position: relative; z-index: 1; font-weight: 600;">“为什么我们给组件命名时不多遵从自然语言呢？”</p></blockquote><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: relative; z-index: 1;">在自然的英文里，形容词和其它描述语通常都出现在名词之前，否则需要使用连接词。比如：</p><ul style="line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: inherit; z-index: 1; padding-left: 1.5em;"><li>Coffee<span>&nbsp;</span><em style="color: rgb(79, 89, 89);">with</em><span>&nbsp;</span>milk</li><li>Soup<span>&nbsp;</span><em style="color: rgb(79, 89, 89);">of the</em><span>&nbsp;</span>day</li><li>Visitor<span>&nbsp;</span><em style="color: rgb(79, 89, 89);">to the</em><span>&nbsp;</span>museum</li></ul><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: relative; z-index: 1;">如果你愿意，你完全可以在组件名里包含这些连接词，但是单词的顺序很重要。</p><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: relative; z-index: 1;">同样要注意<strong style="font-weight: 600; color: rgb(39, 56, 73);">在你的应用中所谓的“高级别”是跟语境有关的</strong>。比如对于一个带搜索表单的应用来说，它可能包含这样的组件：</p><pre style="border-radius: 2px; position: relative; font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85em; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial;"><code class="hljs undefined" style="font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85rem; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial; color: rgb(82, 82, 82); padding: 1.2em 1.4em; margin: 0px 2px; border-radius: 2px; white-space: pre; overflow-x: auto; line-height: 1.6rem; display: block;">components/
|- ClearSearchButton.vue
|- ExcludeFromSearchInput.vue
|- LaunchOnStartupCheckbox.vue
|- RunSearchButton.vue
|- SearchInput.vue
|- TermsCheckbox.vue</code></pre><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: relative; z-index: 1;">你可能注意到了，我们很难看出来哪些组件是针对搜索的。现在我们来根据规则给组件重新命名：</p><pre style="border-radius: 2px; position: relative; font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85em; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial;"><code class="hljs undefined" style="font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85rem; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial; color: rgb(82, 82, 82); padding: 1.2em 1.4em; margin: 0px 2px; border-radius: 2px; white-space: pre; overflow-x: auto; line-height: 1.6rem; display: block;">components/
|- SearchButtonClear.vue
|- SearchButtonRun.vue
|- SearchInputExcludeGlob.vue
|- SearchInputQuery.vue
|- SettingsCheckboxLaunchOnStartup.vue
|- SettingsCheckboxTerms.vue</code></pre><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: relative; z-index: 1;">因为编辑器通常会按字母顺序组织文件，所以现在组件之间的重要关系一目了然。</p><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: relative; z-index: 1;">你可能想换成多级目录的方式，把所有的搜索组件放到“search”目录，把所有的设置组件放到“settings”目录。我们只推荐在非常大型 (如有 100+ 个组件) 的应用下才考虑这么做，因为：</p><ul style="line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: inherit; z-index: 1; padding-left: 1.5em;"><li>在多级目录间找来找去，要比在单个<span>&nbsp;</span><code style="font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85em; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial; color: rgb(214, 50, 0); padding: 3px 5px; margin: 0px 2px; border-radius: 2px; white-space: nowrap;">components</code><span>&nbsp;</span>目录下滚动查找要花费更多的精力。</li><li>存在组件重名 (比如存在多个<span>&nbsp;</span><code style="font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85em; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial; color: rgb(214, 50, 0); padding: 3px 5px; margin: 0px 2px; border-radius: 2px; white-space: nowrap;">ButtonDelete</code><span>&nbsp;</span>组件) 的时候在编辑器里更难快速定位。</li><li>让重构变得更难，因为为一个移动了的组件更新相关引用时，查找/替换通常并不高效。</li></ul></details>

#### 反例

```
components/
|- ClearSearchButton.vue
|- ExcludeFromSearchInput.vue
|- LaunchOnStartupCheckbox.vue
|- RunSearchButton.vue
|- SearchInput.vue
|- TermsCheckbox.vue
```

#### 好例子

```
components/
|- SearchButtonClear.vue
|- SearchButtonRun.vue
|- SearchInputQuery.vue
|- SearchInputExcludeGlob.vue
|- SettingsCheckboxTerms.vue
|- SettingsCheckboxLaunchOnStartup.vue
```



## 自闭合组件

**在[单文件组件](https://cn.vuejs.org/v2/guide/single-file-components.html)、字符串模板和 [JSX](https://cn.vuejs.org/v2/guide/render-function.html#JSX) 中没有内容的组件应该是自闭合的——但在 DOM 模板里永远不要这样做。**

自闭合组件表示它们不仅没有内容，而且**刻意**没有内容。其不同之处就好像书上的一页白纸对比贴有“本页有意留白”标签的白纸。而且没有了额外的闭合标签，你的代码也更简洁。

不幸的是，HTML 并不支持自闭合的自定义元素——只有[官方的“空”元素](https://www.w3.org/TR/html/syntax.html#void-elements)。所以上述策略仅适用于进入 DOM 之前 Vue 的模板编译器能够触达的地方，然后再产出符合 DOM 规范的 HTML。

#### 反例

```
<!-- 在单文件组件、字符串模板和 JSX 中 -->
<MyComponent></MyComponent>
<!-- 在 DOM 模板中 -->
<my-component/>
```

#### 好例子

```
<!-- 在单文件组件、字符串模板和 JSX 中 -->
<MyComponent/>
<!-- 在 DOM 模板中 -->
<my-component></my-component>
```





## 模板中的组件名大小写

**对于绝大多数项目来说，在[单文件组件](https://cn.vuejs.org/v2/guide/single-file-components.html)和字符串模板中组件名应该总是 PascalCase 的——但是在 DOM 模板中总是 kebab-case 的。**

PascalCase 相比 kebab-case 有一些优势：

- 编辑器可以在模板里自动补全组件名，因为 PascalCase 同样适用于 JavaScript。
- `<MyComponent>` 视觉上比 `<my-component>` 更能够和单个单词的 HTML 元素区别开来，因为前者的不同之处有两个大写字母，后者只有一个横线。
- 如果你在模板中使用任何非 Vue 的自定义元素，比如一个 Web Component，PascalCase 确保了你的 Vue 组件在视觉上仍然是易识别的。

不幸的是，由于 HTML 是大小写不敏感的，在 `DOM 模板中必须仍使用 kebab-case`。

还请注意，如果你已经是 kebab-case 的重度用户，那么与 HTML 保持一致的命名约定且在多个项目中保持相同的大小写规则就可能比上述优势更为重要了。在这些情况下，**在所有的地方都使用 kebab-case 同样是可以接受的。**

#### 反例

```
<!-- 在单文件组件和字符串模板中 -->
<mycomponent/>
<!-- 在单文件组件和字符串模板中 -->
<myComponent/>
<!-- 在 DOM 模板中 -->
<MyComponent></MyComponent>
```

#### 好例子

```
<!-- 在单文件组件和字符串模板中 -->
<MyComponent/>
<!-- 在 DOM 模板中 -->
<my-component></my-component>
<!-- 或者 -->
<!-- 在所有地方 -->
<my-component></my-component>  
```

#### 团队约定

~~~
<!-- 在单文件组件和字符串模板中 -->
<MyComponent/>
<!-- 在 DOM 模板中 -->
<my-component></my-component>
~~~



## JS/JSX 中的组件名大小写

**JS/[JSX](https://cn.vuejs.org/v2/guide/render-function.html#JSX) 中的组件名应该始终是 PascalCase 的，尽管在较为简单的应用中只使用 `Vue.component` 进行全局组件注册时，可以使用 kebab-case 字符串。**

<details open="" style="border-radius: 2px; margin: 1.6em 0px; padding: 1.6em; background-color: rgb(238, 238, 238); display: block; position: relative; color: rgb(48, 68, 85); font-family: &quot;Source Sans Pro&quot;, &quot;Helvetica Neue&quot;, Arial, sans-serif; font-size: 16px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary style="cursor: pointer; padding: 1.6em; margin: -1.6em; outline: none;"><h4 style="font-weight: 600; color: rgb(39, 56, 73); margin: 0px; display: inline-block;">详解</h4></summary><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: relative; z-index: 1;">在 JavaScript 中，PascalCase 是类和构造函数 (本质上任何可以产生多份不同实例的东西) 的命名约定。Vue 组件也有多份实例，所以同样使用 PascalCase 是有意义的。额外的好处是，在 JSX (和模板) 里使用 PascalCase 使得代码的读者更容易分辨 Vue 组件和 HTML 元素。</p><p style="word-spacing: 0.05em; line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: relative; z-index: 1;">然而，对于<strong style="font-weight: 600; color: rgb(39, 56, 73);">只</strong>通过<span>&nbsp;</span><code style="font-family: &quot;Roboto Mono&quot;, Monaco, courier, monospace; font-size: 0.85em; background-color: rgb(248, 248, 248); -webkit-font-smoothing: initial; color: rgb(214, 50, 0); padding: 3px 5px; margin: 0px 2px; border-radius: 2px; white-space: nowrap;">Vue.component</code><span>&nbsp;</span>定义全局组件的应用来说，我们推荐 kebab-case 作为替代。原因是：</p><ul style="line-height: 1.6em; margin: 1.2em 0px -1.2em; padding-bottom: 1.2em; position: inherit; z-index: 1; padding-left: 1.5em;"><li>全局组件很少被 JavaScript 引用，所以遵守 JavaScript 的命名约定意义不大。</li><li>这些应用往往包含许多 DOM 内的模板，这种情况下是<a href="https://cn.vuejs.org/v2/style-guide/#%E6%A8%A1%E6%9D%BF%E4%B8%AD%E7%9A%84%E7%BB%84%E4%BB%B6%E5%90%8D%E5%A4%A7%E5%B0%8F%E5%86%99-%E5%BC%BA%E7%83%88%E6%8E%A8%E8%8D%90" style="text-decoration: none; color: rgb(66, 185, 131); font-weight: 600;"><strong style="font-weight: 600; color: rgb(39, 56, 73);">必须</strong>使用 kebab-case</a><span>&nbsp;</span>的。</li></ul></details>

#### 反例

```
Vue.component('myComponent', {
  // ...
})
import myComponent from './MyComponent.vue'
export default {
  name: 'myComponent',
  // ...
}
export default {
  name: 'my-component',
  // ...
}
```

#### 好例子

```
Vue.component('MyComponent', {
  // ...
})
Vue.component('my-component', {
  // ...
})
import MyComponent from './MyComponent.vue'
export default {
  name: 'MyComponent',
  // ...
}
```





## 完整单词的组件名

编辑器中的自动补全已经让书写长命名的代价非常之低了，而其带来的明确性却是非常宝贵的。不常用的缩写尤其应该避免。

#### 反例

```
components/
|- SdSettings.vue
|- UProfOpts.vue
```

#### 好例子

```
components/
|- StudentDashboardSettings.vue
|- UserProfileOptions.vue
```



## Prop 名大小写

**在声明 prop 的时候，其命名应该始终使用 camelCase，而在模板和 [JSX](https://cn.vuejs.org/v2/guide/render-function.html#JSX) 中应该始终使用 kebab-case。**

我们单纯的遵循每个语言的约定。**`在 JavaScript 中更自然的是 camelCase。而在 HTML 中则是 kebab-case`**。

#### 反例

```
props: {
  'greeting-text': String
}
<WelcomeMessage greetingText="hi"/>
```

#### 好例子

```
props: {
  greetingText: String
}
<WelcomeMessage greeting-text="hi"/>
```





