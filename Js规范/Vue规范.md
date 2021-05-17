# Vue规范

## Prop 定义

**Prop 定义应尽量详细**

在你提交的代码中，prop 的定义应该尽量详细，至少需要指定其类型。

<details data-v-1aedbe13="" class="custom-block details" open="" style="padding: 1.6em; border-left-width: 0.5rem; border-left-style: solid; position: relative; border-radius: 2px; margin: 1.6em 0px; display: block; background-color: rgb(238, 238, 238); color: rgb(44, 62, 80); font-family: Inter, Roboto, Oxygen, &quot;Fira Sans&quot;, &quot;Helvetica Neue&quot;, sans-serif; font-size: 16px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary data-v-1aedbe13="" style="outline: none; cursor: pointer; font-weight: 700 !important;">详解</summary><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">细致的<span>&nbsp;</span><a data-v-1aedbe13="" href="https://cn.vuejs.org/v2/guide/components-props.html#Prop-%E9%AA%8C%E8%AF%81" target="_blank" rel="noopener noreferrer" style="padding: 0px; margin: 0px; font-weight: 700; text-decoration: none; color: rgb(62, 175, 124);">prop 定义<svg data-v-1aedbe13="" xmlns="http://www.w3.org/2000/svg" aria-hidden="true" x="0px" y="0px" viewBox="0 0 100 100" width="15" height="15" class="icon outbound"><path data-v-1aedbe13="" fill="currentColor" d="M18.8,85.1h56l0,0c2.2,0,4-1.8,4-4v-32h-8v28h-48v-48h28v-8h-32l0,0c-2.2,0-4,1.8-4,4v56C14.8,83.3,16.6,85.1,18.8,85.1z"></path><polygon data-v-1aedbe13="" fill="currentColor" points="45.7,48.7 51.3,54.3 77.2,28.5 77.2,37.2 85.2,37.2 85.2,14.9 62.8,14.9 62.8,22.9 71.5,22.9"></polygon></svg></a>有两个好处：</p><ul data-v-1aedbe13="" style="padding-left: 1.2em; line-height: 1.7;"><li data-v-1aedbe13="">它们写明了组件的 API，所以很容易看懂组件的用法；</li><li data-v-1aedbe13="">在开发环境下，如果向一个组件提供格式不正确的 prop，Vue 将会告警，以帮助你捕获潜在的错误来源。</li></ul></details>

#### 反例

```js
// 这样做只有开发原型系统时可以接受
props: ['status']
```

#### 好例子

```js
props: {
  status: String
}
```

```js
// 更好的例子
props: {
  status: {
    type: String,
    required: true,

    validator: value => {
      return [
        'syncing',
        'synced',
        'version-conflict',
        'error'
      ].includes(value)
    }
  }
}
```



## 为 `v-for` 设置 key 值

**总是用 `key` 配合 `v-for`**

在组件上总是必须用 `key` 配合 `v-for`，以便维护内部组件及其子树的状态。甚至在元素上维护可预测的行为，比如动画中的[对象固化 (object constancy)](https://bost.ocks.org/mike/constancy/) ，也是一种好的做法。

<details data-v-1aedbe13="" class="custom-block details" open="" style="padding: 1.6em; border-left-width: 0.5rem; border-left-style: solid; position: relative; border-radius: 2px; margin: 1.6em 0px; display: block; background-color: rgb(238, 238, 238); color: rgb(44, 62, 80); font-family: Inter, Roboto, Oxygen, &quot;Fira Sans&quot;, &quot;Helvetica Neue&quot;, sans-serif; font-size: 16px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary data-v-1aedbe13="" style="outline: none; cursor: pointer; font-weight: 700 !important;">详解</summary><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">假设你有一个待办事项列表：</p><div data-v-1aedbe13="" class="language-js line-numbers-mode" style="position: relative; background-color: rgb(246, 246, 246); border-radius: 6px;"><pre data-v-1aedbe13="" class="language-js" style="line-height: 1.4; padding: 1.25rem 1.5rem 1.25rem 4.5rem; margin: 0.85rem 0px; background: transparent; border-radius: 6px; overflow: auto; position: relative; z-index: 1; vertical-align: middle;"><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(58, 56, 93); padding: 0px; margin: 0px; font-size: 0.85em; background-color: transparent; border-radius: 0px;"><span data-v-1aedbe13="" class="token function" style="padding: 0px; margin: 0px; color: rgb(194, 82, 5);">data</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">(</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">)</span> <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">{</span>
  <span data-v-1aedbe13="" class="token keyword" style="padding: 0px; margin: 0px; color: rgb(185, 45, 188);">return</span> <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">{</span>
    todos<span data-v-1aedbe13="" class="token operator" style="padding: 0px; margin: 0px; color: rgb(11, 126, 125);">:</span> <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">[</span>
      <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">{</span>
        id<span data-v-1aedbe13="" class="token operator" style="padding: 0px; margin: 0px; color: rgb(11, 126, 125);">:</span> <span data-v-1aedbe13="" class="token number" style="padding: 0px; margin: 0px; color: rgb(194, 82, 5);">1</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">,</span>
        text<span data-v-1aedbe13="" class="token operator" style="padding: 0px; margin: 0px; color: rgb(11, 126, 125);">:</span> <span data-v-1aedbe13="" class="token string" style="padding: 0px; margin: 0px; color: rgb(10, 122, 52);">'Learn to use v-for'</span>
      <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">}</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">,</span>
      <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">{</span>
        id<span data-v-1aedbe13="" class="token operator" style="padding: 0px; margin: 0px; color: rgb(11, 126, 125);">:</span> <span data-v-1aedbe13="" class="token number" style="padding: 0px; margin: 0px; color: rgb(194, 82, 5);">2</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">,</span>
        text<span data-v-1aedbe13="" class="token operator" style="padding: 0px; margin: 0px; color: rgb(11, 126, 125);">:</span> <span data-v-1aedbe13="" class="token string" style="padding: 0px; margin: 0px; color: rgb(10, 122, 52);">'Learn to use key'</span>
      <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">}</span>
    <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">]</span>
  <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">}</span>
<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">}</span>
</code></pre><div data-v-1aedbe13="" class="line-numbers-wrapper" style="position: absolute; top: 0px; width: 3.5rem; text-align: center; color: rgb(196, 196, 198); padding: 1.25rem 0px; line-height: 1.4; background-color: rgb(246, 246, 246); border-right: 1px solid rgb(231, 230, 230);"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">1</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">2</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">3</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">4</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">5</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">6</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">7</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">8</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">9</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">10</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">11</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">12</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">13</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">14</span><br data-v-1aedbe13="" style="user-select: none;"></div></div><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">然后你把它们按照字母顺序排序。在更新 DOM 的时候，Vue 将会优化渲染把可能的 DOM 变更降到最低。即可能删掉第一个待办事项元素，然后把它重新加回到列表的最末尾。</p><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">这里的问题在于，不要删除仍然会留在 DOM 中的元素。比如你想使用<span>&nbsp;</span><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">&lt;transition-group&gt;</code><span>&nbsp;</span>给列表加过渡动画，或想在被渲染元素是<span>&nbsp;</span><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">&lt;input&gt;</code><span>&nbsp;</span>时保持聚焦。在这些情况下，为每一个项目添加一个唯一的键值 (比如<span>&nbsp;</span><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">:key="todo.id"</code>) 将会让 Vue 知道如何使行为更容易预测。</p><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">根据我们的经验，最好<em data-v-1aedbe13="">始终</em>添加一个唯一的键值，以便你和你的团队永远不必担心这些极端情况。也在少数对性能有严格要求的情况下，为了避免对象固化，你可以刻意做一些非常规的处理。</p></details>

#### 反例

```html
<ul>
  <li v-for="todo in todos">
    {{ todo.text }}
  </li>
</ul>
```

#### 好例子

```html
<ul>
  <li
    v-for="todo in todos"
    :key="todo.id"
  >
    {{ todo.text }}
  </li>
</ul>
```





## 避免 `v-if` 和 `v-for` 一起使用

**永远不要把 `v-if` 和 `v-for` 同时用在同一个元素上。**

一般我们在两种常见的情况下会倾向于这样做：

- 为了过滤一个列表中的项目 (比如 `v-for="user in users" v-if="user.isActive"`)。在这种情形下，请将 `users` 替换为一个计算属性 (比如 `activeUsers`)，让其返回过滤后的列表。
- 为了避免渲染本应该被隐藏的列表 (比如 `v-for="user in users" v-if="shouldShowUsers"`)。这种情形下，请将 `v-if` 移动至容器元素上 (比如 `ul`、`ol`

<details data-v-1aedbe13="" class="custom-block details" open="" style="padding: 1.6em; border-left-width: 0.5rem; border-left-style: solid; position: relative; border-radius: 2px; margin: 1.6em 0px; display: block; background-color: rgb(238, 238, 238); color: rgb(44, 62, 80); font-family: Inter, Roboto, Oxygen, &quot;Fira Sans&quot;, &quot;Helvetica Neue&quot;, sans-serif; font-size: 16px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary data-v-1aedbe13="" style="outline: none; cursor: pointer; font-weight: 700 !important;">详解</summary><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">当 Vue 处理指令时，<code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">v-for</code><span>&nbsp;</span>比<span>&nbsp;</span><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">v-if</code><span>&nbsp;</span>具有更高的优先级，所以这个模板：</p><div data-v-1aedbe13="" class="language-html line-numbers-mode" style="position: relative; background-color: rgb(246, 246, 246); border-radius: 6px;"><pre data-v-1aedbe13="" class="language-html" style="line-height: 1.4; padding: 1.25rem 1.5rem 1.25rem 4.5rem; margin: 0.85rem 0px; background: transparent; border-radius: 6px; overflow: auto; position: relative; z-index: 1; vertical-align: middle;"><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(58, 56, 93); padding: 0px; margin: 0px; font-size: 0.85em; background-color: transparent; border-radius: 0px;"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&lt;</span>ul</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&gt;</span></span>
  <span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&lt;</span>li</span>
    <span data-v-1aedbe13="" class="token attr-name" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);">v-for</span><span data-v-1aedbe13="" class="token attr-value" style="padding: 0px; margin: 0px; color: rgb(10, 122, 52);"><span data-v-1aedbe13="" class="token punctuation attr-equals" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">=</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span>user in users<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span></span>
    <span data-v-1aedbe13="" class="token attr-name" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);">v-if</span><span data-v-1aedbe13="" class="token attr-value" style="padding: 0px; margin: 0px; color: rgb(10, 122, 52);"><span data-v-1aedbe13="" class="token punctuation attr-equals" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">=</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span>user.isActive<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span></span>
    <span data-v-1aedbe13="" class="token attr-name" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);">:key</span><span data-v-1aedbe13="" class="token attr-value" style="padding: 0px; margin: 0px; color: rgb(10, 122, 52);"><span data-v-1aedbe13="" class="token punctuation attr-equals" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">=</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span>user.id<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span></span>
  <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&gt;</span></span>
    {{ user.name }}
  <span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&lt;/</span>li</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&gt;</span></span>
<span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&lt;/</span>ul</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&gt;</span></span>
</code></pre><div data-v-1aedbe13="" class="line-numbers-wrapper" style="position: absolute; top: 0px; width: 3.5rem; text-align: center; color: rgb(196, 196, 198); padding: 1.25rem 0px; line-height: 1.4; background-color: rgb(246, 246, 246); border-right: 1px solid rgb(231, 230, 230);"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">1</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">2</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">3</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">4</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">5</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">6</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">7</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">8</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">9</span><br data-v-1aedbe13="" style="user-select: none;"></div></div><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">将会经过如下运算：</p><div data-v-1aedbe13="" class="language-js line-numbers-mode" style="position: relative; background-color: rgb(246, 246, 246); border-radius: 6px;"><pre data-v-1aedbe13="" class="language-js" style="line-height: 1.4; padding: 1.25rem 1.5rem 1.25rem 4.5rem; margin: 0.85rem 0px; background: transparent; border-radius: 6px; overflow: auto; position: relative; z-index: 1; vertical-align: middle;"><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(58, 56, 93); padding: 0px; margin: 0px; font-size: 0.85em; background-color: transparent; border-radius: 0px;"><span data-v-1aedbe13="" class="token keyword" style="padding: 0px; margin: 0px; color: rgb(185, 45, 188);">this</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">.</span>users<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">.</span><span data-v-1aedbe13="" class="token function" style="padding: 0px; margin: 0px; color: rgb(194, 82, 5);">map</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">(</span><span data-v-1aedbe13="" class="token parameter" style="padding: 0px; margin: 0px;">user</span> <span data-v-1aedbe13="" class="token operator" style="padding: 0px; margin: 0px; color: rgb(11, 126, 125);">=&gt;</span> <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">{</span>
  <span data-v-1aedbe13="" class="token keyword" style="padding: 0px; margin: 0px; color: rgb(185, 45, 188);">if</span> <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">(</span>user<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">.</span>isActive<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">)</span> <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">{</span>
    <span data-v-1aedbe13="" class="token keyword" style="padding: 0px; margin: 0px; color: rgb(185, 45, 188);">return</span> user<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">.</span>name
  <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">}</span>
<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">}</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">)</span>
</code></pre><div data-v-1aedbe13="" class="line-numbers-wrapper" style="position: absolute; top: 0px; width: 3.5rem; text-align: center; color: rgb(196, 196, 198); padding: 1.25rem 0px; line-height: 1.4; background-color: rgb(246, 246, 246); border-right: 1px solid rgb(231, 230, 230);"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">1</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">2</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">3</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">4</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">5</span><br data-v-1aedbe13="" style="user-select: none;"></div></div><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">因此哪怕我们只渲染出一小部分用户的元素，也得在每次重渲染的时候遍历整个列表，不论活跃用户是否发生了变化。</p><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">通过将其更换为在如下的一个计算属性上遍历：</p><div data-v-1aedbe13="" class="language-js line-numbers-mode" style="position: relative; background-color: rgb(246, 246, 246); border-radius: 6px;"><pre data-v-1aedbe13="" class="language-js" style="line-height: 1.4; padding: 1.25rem 1.5rem 1.25rem 4.5rem; margin: 0.85rem 0px; background: transparent; border-radius: 6px; overflow: auto; position: relative; z-index: 1; vertical-align: middle;"><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(58, 56, 93); padding: 0px; margin: 0px; font-size: 0.85em; background-color: transparent; border-radius: 0px;">computed<span data-v-1aedbe13="" class="token operator" style="padding: 0px; margin: 0px; color: rgb(11, 126, 125);">:</span> <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">{</span>
  <span data-v-1aedbe13="" class="token function" style="padding: 0px; margin: 0px; color: rgb(194, 82, 5);">activeUsers</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">(</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">)</span> <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">{</span>
    <span data-v-1aedbe13="" class="token keyword" style="padding: 0px; margin: 0px; color: rgb(185, 45, 188);">return</span> <span data-v-1aedbe13="" class="token keyword" style="padding: 0px; margin: 0px; color: rgb(185, 45, 188);">this</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">.</span>users<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">.</span><span data-v-1aedbe13="" class="token function" style="padding: 0px; margin: 0px; color: rgb(194, 82, 5);">filter</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">(</span><span data-v-1aedbe13="" class="token parameter" style="padding: 0px; margin: 0px;">user</span> <span data-v-1aedbe13="" class="token operator" style="padding: 0px; margin: 0px; color: rgb(11, 126, 125);">=&gt;</span> user<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">.</span>isActive<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">)</span>
  <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">}</span>
<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">}</span>
</code></pre><div data-v-1aedbe13="" class="line-numbers-wrapper" style="position: absolute; top: 0px; width: 3.5rem; text-align: center; color: rgb(196, 196, 198); padding: 1.25rem 0px; line-height: 1.4; background-color: rgb(246, 246, 246); border-right: 1px solid rgb(231, 230, 230);"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">1</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">2</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">3</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">4</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">5</span><br data-v-1aedbe13="" style="user-select: none;"></div></div><div data-v-1aedbe13="" class="language-html line-numbers-mode" style="position: relative; background-color: rgb(246, 246, 246); border-radius: 6px;"><pre data-v-1aedbe13="" class="language-html" style="line-height: 1.4; padding: 1.25rem 1.5rem 1.25rem 4.5rem; margin: 0.85rem 0px; background: transparent; border-radius: 6px; overflow: auto; position: relative; z-index: 1; vertical-align: middle;"><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(58, 56, 93); padding: 0px; margin: 0px; font-size: 0.85em; background-color: transparent; border-radius: 0px;"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&lt;</span>ul</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&gt;</span></span>
  <span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&lt;</span>li</span>
    <span data-v-1aedbe13="" class="token attr-name" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);">v-for</span><span data-v-1aedbe13="" class="token attr-value" style="padding: 0px; margin: 0px; color: rgb(10, 122, 52);"><span data-v-1aedbe13="" class="token punctuation attr-equals" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">=</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span>user in activeUsers<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span></span>
    <span data-v-1aedbe13="" class="token attr-name" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);">:key</span><span data-v-1aedbe13="" class="token attr-value" style="padding: 0px; margin: 0px; color: rgb(10, 122, 52);"><span data-v-1aedbe13="" class="token punctuation attr-equals" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">=</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span>user.id<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span></span>
  <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&gt;</span></span>
    {{ user.name }}
  <span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&lt;/</span>li</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&gt;</span></span>
<span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&lt;/</span>ul</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&gt;</span></span>
</code></pre><div data-v-1aedbe13="" class="line-numbers-wrapper" style="position: absolute; top: 0px; width: 3.5rem; text-align: center; color: rgb(196, 196, 198); padding: 1.25rem 0px; line-height: 1.4; background-color: rgb(246, 246, 246); border-right: 1px solid rgb(231, 230, 230);"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">1</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">2</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">3</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">4</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">5</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">6</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">7</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">8</span><br data-v-1aedbe13="" style="user-select: none;"></div></div><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">我们将会获得如下好处：</p><ul data-v-1aedbe13="" style="padding-left: 1.2em; line-height: 1.7;"><li data-v-1aedbe13="">过滤后的列表<em data-v-1aedbe13="">只</em>会在<span>&nbsp;</span><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">users</code><span>&nbsp;</span>数组发生相关变化时才被重新运算，过滤更高效。</li><li data-v-1aedbe13="">使用<span>&nbsp;</span><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">v-for="user in activeUsers"</code><span>&nbsp;</span>之后，我们在渲染的时候<em data-v-1aedbe13="">只</em>遍历活跃用户，渲染更高效。</li><li data-v-1aedbe13="">解耦渲染层的逻辑，可维护性 (对逻辑的更改和扩展) 更强。</li></ul><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">为了获得同样的好处，我们也可以把：</p><div data-v-1aedbe13="" class="language-html line-numbers-mode" style="position: relative; background-color: rgb(246, 246, 246); border-radius: 6px;"><pre data-v-1aedbe13="" class="language-html" style="line-height: 1.4; padding: 1.25rem 1.5rem 1.25rem 4.5rem; margin: 0.85rem 0px; background: transparent; border-radius: 6px; overflow: auto; position: relative; z-index: 1; vertical-align: middle;"><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(58, 56, 93); padding: 0px; margin: 0px; font-size: 0.85em; background-color: transparent; border-radius: 0px;"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&lt;</span>ul</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&gt;</span></span>
  <span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&lt;</span>li</span>
    <span data-v-1aedbe13="" class="token attr-name" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);">v-for</span><span data-v-1aedbe13="" class="token attr-value" style="padding: 0px; margin: 0px; color: rgb(10, 122, 52);"><span data-v-1aedbe13="" class="token punctuation attr-equals" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">=</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span>user in users<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span></span>
    <span data-v-1aedbe13="" class="token attr-name" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);">v-if</span><span data-v-1aedbe13="" class="token attr-value" style="padding: 0px; margin: 0px; color: rgb(10, 122, 52);"><span data-v-1aedbe13="" class="token punctuation attr-equals" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">=</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span>shouldShowUsers<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span></span>
    <span data-v-1aedbe13="" class="token attr-name" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);">:key</span><span data-v-1aedbe13="" class="token attr-value" style="padding: 0px; margin: 0px; color: rgb(10, 122, 52);"><span data-v-1aedbe13="" class="token punctuation attr-equals" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">=</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span>user.id<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span></span>
  <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&gt;</span></span>
    {{ user.name }}
  <span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&lt;/</span>li</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&gt;</span></span>
<span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&lt;/</span>ul</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&gt;</span></span>
</code></pre><div data-v-1aedbe13="" class="line-numbers-wrapper" style="position: absolute; top: 0px; width: 3.5rem; text-align: center; color: rgb(196, 196, 198); padding: 1.25rem 0px; line-height: 1.4; background-color: rgb(246, 246, 246); border-right: 1px solid rgb(231, 230, 230);"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">1</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">2</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">3</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">4</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">5</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">6</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">7</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">8</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">9</span><br data-v-1aedbe13="" style="user-select: none;"></div></div><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">更新为：</p><div data-v-1aedbe13="" class="language-html line-numbers-mode" style="position: relative; background-color: rgb(246, 246, 246); border-radius: 6px;"><pre data-v-1aedbe13="" class="language-html" style="line-height: 1.4; padding: 1.25rem 1.5rem 1.25rem 4.5rem; margin: 0.85rem 0px; background: transparent; border-radius: 6px; overflow: auto; position: relative; z-index: 1; vertical-align: middle;"><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(58, 56, 93); padding: 0px; margin: 0px; font-size: 0.85em; background-color: transparent; border-radius: 0px;"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&lt;</span>ul</span> <span data-v-1aedbe13="" class="token attr-name" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);">v-if</span><span data-v-1aedbe13="" class="token attr-value" style="padding: 0px; margin: 0px; color: rgb(10, 122, 52);"><span data-v-1aedbe13="" class="token punctuation attr-equals" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">=</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span>shouldShowUsers<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span></span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&gt;</span></span>
  <span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&lt;</span>li</span>
    <span data-v-1aedbe13="" class="token attr-name" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);">v-for</span><span data-v-1aedbe13="" class="token attr-value" style="padding: 0px; margin: 0px; color: rgb(10, 122, 52);"><span data-v-1aedbe13="" class="token punctuation attr-equals" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">=</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span>user in users<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span></span>
    <span data-v-1aedbe13="" class="token attr-name" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);">:key</span><span data-v-1aedbe13="" class="token attr-value" style="padding: 0px; margin: 0px; color: rgb(10, 122, 52);"><span data-v-1aedbe13="" class="token punctuation attr-equals" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">=</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span>user.id<span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">"</span></span>
  <span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&gt;</span></span>
    {{ user.name }}
  <span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&lt;/</span>li</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&gt;</span></span>
<span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token tag" style="padding: 0px; margin: 0px; color: rgb(178, 8, 95);"><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&lt;/</span>ul</span><span data-v-1aedbe13="" class="token punctuation" style="padding: 0px; margin: 0px; color: rgb(168, 169, 204);">&gt;</span></span>
</code></pre><div data-v-1aedbe13="" class="line-numbers-wrapper" style="position: absolute; top: 0px; width: 3.5rem; text-align: center; color: rgb(196, 196, 198); padding: 1.25rem 0px; line-height: 1.4; background-color: rgb(246, 246, 246); border-right: 1px solid rgb(231, 230, 230);"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">1</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">2</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">3</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">4</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">5</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">6</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">7</span><br data-v-1aedbe13="" style="user-select: none;"><span data-v-1aedbe13="" class="line-number" style="padding: 0px; margin: 0px; font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; position: relative; z-index: 4; user-select: none; font-size: 0.85em;">8</span><br data-v-1aedbe13="" style="user-select: none;"></div></div><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">通过将<span>&nbsp;</span><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">v-if</code><span>&nbsp;</span>移动到容器元素，我们不会再对列表中的每个用户检查<span>&nbsp;</span><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">shouldShowUsers</code>。取而代之的是，我们只检查它一次，且不会在<span>&nbsp;</span><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">shouldShowUsers</code><span>&nbsp;</span>为否的时候运算<span>&nbsp;</span><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">v-for</code>。</p></details>

#### 反例

```html
<ul>
  <li
    v-for="user in users"
    v-if="user.isActive"
    :key="user.id"
  >
    {{ user.name }}
  </li>
</ul>
```

```html
<ul>
  <li
    v-for="user in users"
    v-if="shouldShowUsers"
    :key="user.id"
  >
    {{ user.name }}
  </li>
</ul>
```

#### 好例子

```html
<ul>
  <li
    v-for="user in activeUsers"
    :key="user.id"
  >
    {{ user.name }}
  </li>
</ul>
```

```html
<ul v-if="shouldShowUsers">
  <li
    v-for="user in users"
    :key="user.id"
  >
    {{ user.name }}
  </li>
</ul>
```







## 为组件样式设置作用域

**对于应用来说，顶级 `App` 组件和布局组件中的样式可以是全局的，但是其它所有组件都应该是有作用域的。**

这条规则只和[单文件组件](https://vue3js.cn/docs/zh/guide/single-file-component.html)有关。你*不一定*要使用 [`scoped` attribute](https://vue-loader.vuejs.org/en/features/scoped-css.html)。设置作用域也可以通过 [CSS Modules](https://vue-loader.vuejs.org/en/features/css-modules.html)，那是一个基于 class 的类似 [BEM](http://getbem.com/) 的策略，当然你也可以使用其它的库或约定。

**不管怎样，对于组件库，我们应该更倾向于选用基于 class 的策略而不是 `scoped` attribute。**

这让覆写内部样式更容易：使用了人类可理解的 class 名称且没有太高的选择器优先级，而且不太会导致冲突。

<details data-v-1aedbe13="" class="custom-block details" open="" style="padding: 1.6em; border-left-width: 0.5rem; border-left-style: solid; position: relative; border-radius: 2px; margin: 1.6em 0px; display: block; background-color: rgb(238, 238, 238); color: rgb(44, 62, 80); font-family: Inter, Roboto, Oxygen, &quot;Fira Sans&quot;, &quot;Helvetica Neue&quot;, sans-serif; font-size: 16px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary data-v-1aedbe13="" style="outline: none; cursor: pointer; font-weight: 700 !important;">详解</summary><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">如果你和其他开发者一起开发一个大型工程，或有时引入三方 HTML/CSS (比如来自 Auth0)，设置一致的作用域会确保你的样式只会运用在它们想要作用的组件上。</p><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">不止要使用<span>&nbsp;</span><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">scoped</code><span>&nbsp;</span>attribute，使用唯一的 class 名可以帮你确保那些三方库的 CSS 不会运用在你自己的 HTML 上。比如许多工程都使用了<span>&nbsp;</span><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">button</code>、<code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">btn</code><span>&nbsp;</span>或<span>&nbsp;</span><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">icon</code><span>&nbsp;</span>class 名，所以即便你不使用类似 BEM 的策略，添加一个 app 专属或组件专属的前缀 (比如<span>&nbsp;</span><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">ButtonClose-icon</code>) 也可以提供很多保护。</p></details>

#### 反例

```html
<template>
  <button class="btn btn-close">×</button>
</template>

<style>
.btn-close {
  background-color: red;
}
</style>
```

#### 好例子

```html
<template>
  <button class="button button-close">×</button>
</template>

<!-- 使用 `scoped` attribute -->
<style scoped>
.button {
  border: none;
  border-radius: 2px;
}

.button-close {
  background-color: red;
}
</style>
```

```html
<template>
  <button :class="[$style.button, $style.buttonClose]">×</button>
</template>

<!-- 使用 CSS modules -->
<style module>
.button {
  border: none;
  border-radius: 2px;
}

.buttonClose {
  background-color: red;
}
</style>
```

```html
<template>
  <button class="c-Button c-Button--close">×</button>
</template>

<!-- 使用 BEM 约定 -->
<style>
.c-Button {
  border: none;
  border-radius: 2px;
}

.c-Button--close {
  background-color: red;
}
</style>
```





## 私有 property 名称

**使用模块作用域保持不允许外部访问的函数的私有性。如果无法做到这一点，就始终为插件、混入等不考虑作为对外公共 API 的自定义私有 property 使用 `$_` 前缀。并附带一个命名空间以回避和其它作者的冲突 (比如 `$_yourPluginName_`)。**

::: 详细

Vue 使用 `_` 前缀来定义其自身的私有 property，所以使用相同的前缀 (比如 `_update`) 有覆写实例 property 的风险。即便你检查确认 Vue 当前版本没有用到这个 property 名，也不能保证和将来的版本没有冲突。

对于 `$` 前缀来说，其在 Vue 生态系统中的目的是暴露给用户的一个特殊的实例 property，所以把它用于*私有* property 并不合适。

不过，我们推荐把这两个前缀结合为 `$_`，作为一个用户定义的私有 property 的约定，以确保不会和 Vue 自身相冲突。

:::

#### 反例

```js
const myGreatMixin = {
  // ...
  methods: {
    update() {
      // ...
    }
  }
}
```

```js
const myGreatMixin = {
  // ...
  methods: {
    _update() {
      // ...
    }
  }
}
```

```js
const myGreatMixin = {
  // ...
  methods: {
    $update() {
      // ...
    }
  }
}
```

```js
const myGreatMixin = {
  // ...
  methods: {
    $_update() {
      // ...
    }
  }
}
```

#### 好例子

```js
const myGreatMixin = {
  // ...
  methods: {
    $_myGreatMixin_update() {
      // ...
    }
  }
}
```

```js
// Even better!
const myGreatMixin = {
  // ...
  methods: {
    publicMethod() {
      // ...
      myPrivateFunction()
    }
  }
}

function myPrivateFunction() {
  // ...
}

export default myGreatMixin
```







## 多个 attribute 的元素

**多个 attribute 的元素应该分多行撰写，每个 attribute 一行。**

在 JavaScript 中，用多行分隔对象的多个 property 是很常见的最佳实践，因为这样更易读。模板和 [JSX](https://cn.vuejs.org/v2/guide/render-function.html#JSX) 值得我们做相同的考虑。

#### 反例

```
<img src="https://vuejs.org/images/logo.png" alt="Vue Logo">
<MyComponent foo="a" bar="b" baz="c"/>
```

#### 好例子

```
<img
  src="https://vuejs.org/images/logo.png"
  alt="Vue Logo"
>
<MyComponent
  foo="a"
  bar="b"
  baz="c"
/>
```





## 模板中的简单表达式

**组件模板应该只包含简单的表达式，复杂的表达式则应该重构为计算属性或方法。**

复杂表达式会让你的模板变得不那么声明式。我们应该尽量描述应该出现的*是*什么，而非如何计算那个值。而且计算属性和方法使得代码可以重用。

#### 反例

```html
{{
  fullName.split(' ').map((word) => {
    return word[0].toUpperCase() + word.slice(1)
  }).join(' ')
}}
```



#### 好例子

```html
<!-- 在模板中 -->
{{ normalizedFullName }}
```

```js
// 复杂表达式已经移入一个计算属性
computed: {
  normalizedFullName() {
    return this.fullName.split(' ')
      .map(word => word[0].toUpperCase() + word.slice(1))
      .join(' ')
  }
}
```



## 简单的计算属性

**应该把复杂计算属性分割为尽可能多的更简单的 property。**

<details data-v-1aedbe13="" class="custom-block details" open="" style="padding: 1.6em; border-left-width: 0.5rem; border-left-style: solid; position: relative; border-radius: 2px; margin: 1.6em 0px; display: block; background-color: rgb(238, 238, 238); color: rgb(44, 62, 80); font-family: Inter, Roboto, Oxygen, &quot;Fira Sans&quot;, &quot;Helvetica Neue&quot;, sans-serif; font-size: 16px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary data-v-1aedbe13="" style="outline: none; cursor: pointer; font-weight: 700 !important;">详解</summary><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">更简单、命名得当的计算属性是这样的：</p><ul data-v-1aedbe13="" style="padding-left: 1.2em; line-height: 1.7;"><li data-v-1aedbe13=""><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);"><strong data-v-1aedbe13="" style="font-weight: 700;">易于测试</strong></p><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">当每个计算属性都包含一个非常简单且很少依赖的表达式时，撰写测试以确保其正确工作就会更加容易。</p></li><li data-v-1aedbe13=""><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);"><strong data-v-1aedbe13="" style="font-weight: 700;">易于阅读</strong></p><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">简化计算属性要求你为每一个值都起一个描述性的名称，即便它不可复用。这使得其他开发者 (以及未来的你) 更容易专注在他们关心的代码上并搞清楚发生了什么。</p></li><li data-v-1aedbe13=""><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);"><strong data-v-1aedbe13="" style="font-weight: 700;">更好的“拥抱变化”</strong></p><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">任何能够命名的值都可能用在视图上。举个例子，我们可能打算展示一个信息，告诉用户他们存了多少钱；也可能打算计算税费，但是可能会分开展现，而不是作为总价的一部分。</p><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">小的、专注的计算属性减少了信息使用时的假设性限制，所以需求变更时也用不着那么多重构了。</p></li></ul></details>

#### 反例

```js
computed: {
  price() {
    const basePrice = this.manufactureCost / (1 - this.profitMargin)
    return (
      basePrice -
      basePrice * (this.discountPercent || 0)
    )
  }
}
```

#### 好例子

```js
computed: {
  basePrice() {
    return this.manufactureCost / (1 - this.profitMargin)
  },

  discount() {
    return this.basePrice * (this.discountPercent || 0)
  },

  finalPrice() {
    return this.basePrice - this.discount
  }
}
```





## 带引号的 attribute 值

**非空 HTML attribute 值应该始终带引号 (单引号或双引号，选你 JS 里不用的那个)。**

在 HTML 中不带空格的 attribute 值是可以没有引号的，但这鼓励了大家在特征值里不写空格，导致可读性变差。

#### 反例

```html
<input type=text>
```

```html
<AppSidebar :style={width:sidebarWidth+'px'}>
```

#### 好例子

```html
<input type="text">
```

```html
<AppSidebar :style="{ width: sidebarWidth + 'px' }">
```





## 指令缩写强烈推荐

**指令缩写 (用 `:` 表示 `v-bind:`，`@` 表示 `v-on:` 和用 `#` 表示 `v-slot`) 应该要么都用要么都不用。**

#### 反例

```html
<input
  v-bind:value="newTodoText"
  :placeholder="newTodoInstructions"
>
```



```html
<input
  v-on:input="onInput"
  @focus="onFocus"
>
```



```html
<template v-slot:header>
  <h1>Here might be a page title</h1>
</template>

<template #footer>
  <p>Here's some contact info</p>
</template>
```



#### 好例子

```html
<input
  :value="newTodoText"
  :placeholder="newTodoInstructions"
>
```



```html
<input
  v-bind:value="newTodoText"
  v-bind:placeholder="newTodoInstructions"
>
```



```html
<input
  @input="onInput"
  @focus="onFocus"
>
```



```html
<input
  v-on:input="onInput"
  v-on:focus="onFocus"
>
```



```html
<template v-slot:header>
  <h1>Here might be a page title</h1>
</template>

<template v-slot:footer>
  <p>Here's some contact info</p>
</template>
```



```html
<template #header>
  <h1>Here might be a page title</h1>
</template>

<template #footer>
  <p>Here's some contact info</p>
</template>
```

`团队约定：全部用简写。`





## 组件/实例的选项顺序

**组件/实例的选项应该有统一的顺序。**

这是我们推荐的组件选项默认顺序。它们被划分为几大类，所以你也能知道从插件里添加的新 property 应该放到哪里。

1. **全局感知** (要求组件以外的知识)
   - `name`
2. **模板依赖** (模板内使用的资源)
   - `components`
   - `directives`
3. **组合** (向选项里合并 property)
   - `extends`
   - `mixins`
   - `provide`/`inject`
4. **接口** (组件的接口)
   - `inheritAttrs`
   - `props`
   - `emits`
5. **组合式 API** (使用组合式 API 的入口点)
   - `setup`
6. **Local State** (原生响应式 property)
   - `data`
   - `computed`
7. **事件** (通过响应式事件触发的回调)
   - `watch`
   - 生命周期钩子 (按照它们被调用的顺序)
     - `beforeCreate`
     - `created`
     - `beforeMount`
     - `mounted`
     - `beforeUpdate`
     - `updated`
     - `activated`
     - `deactivated`
     - `beforeUnmount`
     - `unmounted`
     - `errorCaptured`
     - `renderTracked`
     - `renderTriggered`
8. **非响应式的 property** (不依赖响应性系统的实例 property)
   - `methods`
9. **渲染** (组件输出的声明式描述)
   - `template`/`render`





## 元素 attribute 的顺序

**元素 (包括组件) 的 attribute 应该有统一的顺序。**

这是我们为组件选项推荐的默认顺序。它们被划分为几大类，所以你也能知道新添加的自定义 attribute 和指令应该放到哪里。

1. **定义** (提供组件的选项)
   - `is`
2. **列表渲染** (创建多个变化的相同元素)
   - `v-for`
3. **条件渲染** (元素是否渲染/显示)
   - `v-if`
   - `v-else-if`
   - `v-else`
   - `v-show`
   - `v-cloak`
4. **渲染修饰符** (改变元素的渲染方式)
   - `v-pre`
   - `v-once`
5. **全局感知** (需要超越组件的知识)
   - `id`
6. **唯一的 Attributes** (需要唯一值的 attribute)
   - `ref`
   - `key`
7. **双向绑定** (把绑定和事件结合起来)
   - `v-model`
8. **其他 Attributes** (所有普通的绑定或未绑定的 attribute)
9. **事件** (组件事件监听器)
   - `v-on`
10. **内容** (覆写元素的内容)
    - `v-html`
    - `v-text`



## 组件/实例选项中的空行

**你可能想在多个 property 之间增加一个空行，特别是在这些选项一屏放不下，需要滚动才能都看到的时候。**

当你的组件开始觉得密集或难以阅读时，在多个 property 之间添加空行可以让其变得容易。在一些诸如 Vim 的编辑器里，这样格式化后的选项还能通过键盘被快速导航。

#### 好例子

```vue
props: {
  value: {
    type: String,
    required: true
  },

  focused: {
    type: Boolean,
    default: false
  },

  label: String,
  icon: String
},

computed: {
  formattedValue() {
    // ...
  },

  inputClasses() {
    // ...
  }
}
```



```vue
// 没有空行在组件易于阅读和导航时也没问题。
props: {
  value: {
    type: String,
    required: true
  },

  focused: {
    type: Boolean,
    default: false
  },

  label: String,
  icon: String
},

computed: {
  formattedValue() {
    // ...
  },

  inputClasses() {
    // ...
  }
}
```





## 单文件组件的顶级元素的顺序

**[单文件组件](https://vue3js.cn/docs/zh/guide/single-file-component.html)应该总是让 `<script>`、`<template>` 和 `<style>` 标签的顺序保持一致。且 `<style>` 要放在最后，因为另外两个标签至少要有一个。**

#### 反例

```html
<style>/* ... */</style>
<script>/* ... */</script>
<template>...</template>
```



```html
<!-- ComponentA.vue -->
<script>/* ... */</script>
<template>...</template>
<style>/* ... */</style>

<!-- ComponentB.vue -->
<template>...</template>
<script>/* ... */</script>
<style>/* ... */</style>
```



#### 好例子

```html
<!-- ComponentA.vue -->
<script>/* ... */</script>
<template>...</template>
<style>/* ... */</style>

<!-- ComponentB.vue -->
<script>/* ... */</script>
<template>...</template>
<style>/* ... */</style>
```



```html
<!-- ComponentA.vue -->
<template>...</template>
<script>/* ... */</script>
<style>/* ... */</style>

<!-- ComponentB.vue -->
<template>...</template>
<script>/* ... */</script>
<style>/* ... */</style>
```

#### 团队规范

~~~vue
<!-- ComponentA.vue -->
<template>...</template>
<script>/* ... */</script>
<style>/* ... */</style>

<!-- ComponentB.vue -->
<template>...</template>
<script>/* ... */</script>
<style>/* ... */</style>
~~~



## `scoped` 中的元素选择器谨慎使用

**元素选择器应该避免在 `scoped` 中出现。**

在 `scoped` 样式中，类选择器比元素选择器更好，因为大量使用元素选择器是很慢的。

<details data-v-1aedbe13="" class="custom-block details" open="" style="padding: 1.6em; border-left-width: 0.5rem; border-left-style: solid; position: relative; border-radius: 2px; margin: 1.6em 0px; display: block; background-color: rgb(238, 238, 238); color: rgb(44, 62, 80); font-family: Inter, Roboto, Oxygen, &quot;Fira Sans&quot;, &quot;Helvetica Neue&quot;, sans-serif; font-size: 16px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial;"><summary data-v-1aedbe13="" style="outline: none; cursor: pointer; font-weight: 700 !important;">详解</summary><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">为了给样式设置作用域，Vue 会为元素添加一个独一无二的 attribute，例如<span>&nbsp;</span><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">data-v-f3f3eg9</code>。然后修改选择器，使得在匹配选择器的元素中，只有带这个 attribute 才会真正生效 (比如<span>&nbsp;</span><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">button[data-v-f3f3eg9]</code>)。</p><p data-v-1aedbe13="" style="padding: 0px; margin: 0px; line-height: 1.7; margin-block: 1em; margin-inline: 0px; color: rgb(34, 34, 34);">问题在于大量的<a data-v-1aedbe13="" href="http://stevesouders.com/efws/css-selectors/csscreate.php?n=1000&amp;sel=a%5Bhref%5D&amp;body=background%3A+%23CFD&amp;ne=1000" target="_blank" rel="noopener noreferrer" style="padding: 0px; margin: 0px; font-weight: 700; text-decoration: none; color: rgb(62, 175, 124);">元素和 attribute 组合的选择器<svg data-v-1aedbe13="" xmlns="http://www.w3.org/2000/svg" aria-hidden="true" x="0px" y="0px" viewBox="0 0 100 100" width="15" height="15" class="icon outbound"><path data-v-1aedbe13="" fill="currentColor" d="M18.8,85.1h56l0,0c2.2,0,4-1.8,4-4v-32h-8v28h-48v-48h28v-8h-32l0,0c-2.2,0-4,1.8-4,4v56C14.8,83.3,16.6,85.1,18.8,85.1z"></path><polygon data-v-1aedbe13="" fill="currentColor" points="45.7,48.7 51.3,54.3 77.2,28.5 77.2,37.2 85.2,37.2 85.2,14.9 62.8,14.9 62.8,22.9 71.5,22.9"></polygon></svg></a><span>&nbsp;</span>(比如<span>&nbsp;</span><code data-v-1aedbe13="" style="font-family: source-code-pro, Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; color: rgb(71, 101, 130); padding: 0.25rem 0.5rem; margin: 0px; font-size: 0.85em; background-color: rgba(27, 31, 35, 0.05); border-radius: 3px;">button[data-v-f3f3eg9]</code>) 会比<a data-v-1aedbe13="" href="http://stevesouders.com/efws/css-selectors/csscreate.php?n=1000&amp;sel=.class%5Bhref%5D&amp;body=background%3A+%23CFD&amp;ne=1000" target="_blank" rel="noopener noreferrer" style="padding: 0px; margin: 0px; font-weight: 700; text-decoration: none; color: rgb(62, 175, 124);">类和 attribute 组合的选择器<svg data-v-1aedbe13="" xmlns="http://www.w3.org/2000/svg" aria-hidden="true" x="0px" y="0px" viewBox="0 0 100 100" width="15" height="15" class="icon outbound"><path data-v-1aedbe13="" fill="currentColor" d="M18.8,85.1h56l0,0c2.2,0,4-1.8,4-4v-32h-8v28h-48v-48h28v-8h-32l0,0c-2.2,0-4,1.8-4,4v56C14.8,83.3,16.6,85.1,18.8,85.1z"></path><polygon data-v-1aedbe13="" fill="currentColor" points="45.7,48.7 51.3,54.3 77.2,28.5 77.2,37.2 85.2,37.2 85.2,14.9 62.8,14.9 62.8,22.9 71.5,22.9"></polygon></svg></a>慢，所以应该尽可能选用类选择器。</p></details>

#### 反例

```html
<template>
  <button>×</button>
</template>

<style scoped>
button {
  background-color: red;
}
</style>
```



#### 好例子

```html
<template>
  <button class="btn btn-close">×</button>
</template>

<style scoped>
.btn-close {
  background-color: red;
}
</style>
```



## 隐性的父子组件通信

**应该优先通过 prop 和事件进行父子组件之间的通信，而不是 `this.$parent` 或变更 prop。**

一个理想的 Vue 应用是 prop 向下传递，事件向上传递的。遵循这一约定会让你的组件更易于理解。然而，在一些边界情况下 prop 的变更或 `this.$parent` 能够简化两个深度耦合的组件。

问题在于，这种做法在很多*简单*的场景下可能会更方便。但请当心，不要为了一时方便 (少写代码) 而牺牲数据流向的简洁性 (易于理解)。

#### 反例

```js
app.component('TodoItem', {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },

  template: '<input v-model="todo.text">'
})
```



```js
app.component('TodoItem', {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },

  methods: {
    removeTodo() {
      this.$parent.todos = this.$parent.todos.filter(todo => todo.id !== vm.todo.id)
    }
  },

  template: `
    <span>
      {{ todo.text }}
      <button @click="removeTodo">
        ×
      </button>
    </span>
  `
})
```



#### 好例子

```js
app.component('TodoItem', {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },

  template: `
    <input
      :value="todo.text"
      @input="$emit('input', $event.target.value)"
    >
  `
})
```



```js
app.component('TodoItem', {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },

  template: `
    <span>
      {{ todo.text }}
      <button @click="$emit('delete')">
        ×
      </button>
    </span>
  `
})
```



## 非 Flux 的全局状态管理

**应该优先通过 [Vuex](https://github.com/vuejs/vuex) 管理全局状态，而不是通过 `this.$root` 或一个全局事件总线。**

通过 `this.$root` 和/或[全局事件总线管理](https://vuejs.org/v2/guide/migration.html#dispatch-and-broadcast-replaced)状态在很多简单的情况下都是很方便的，但是并不适用于绝大多数的应用。

Vuex 是 Vue 的[官方类 flux 实现](https://vuejs.org/v2/guide/state-management.html#Official-Flux-Like-Implementation)，其提供的不仅是一个管理状态的中心区域，还是组织、追踪和调试状态变更的好工具。它很好地集成在了 Vue 生态系统之中 (包括完整的 [Vue DevTools](https://vuejs.org/v2/guide/installation.html#Vue-Devtools) 支持)。

#### 反例

```js
// main.js
import { createApp } from 'vue'
import mitt from 'mitt'
const app = createApp({
  data() {
    return {
      todos: [],
      emitter: mitt()
    }
  },

  created() {
    this.emitter.on('remove-todo', this.removeTodo)
  },

  methods: {
    removeTodo(todo) {
      const todoIdToRemove = todo.id
      this.todos = this.todos.filter(todo => todo.id !== todoIdToRemove)
    }
  }
})
```



#### 好例子

```js
// store/modules/todos.js
export default {
  state: {
    list: []
  },

  mutations: {
    REMOVE_TODO (state, todoId) {
      state.list = state.list.filter(todo => todo.id !== todoId)
    }
  },

  actions: {
    removeTodo ({ commit, state }, todo) {
      commit('REMOVE_TODO', todo.id)
    }
  }
}
```

```html
<!-- TodoItem.vue -->
<template>
  <span>
    {{ todo.text }}
    <button @click="removeTodo(todo)">
      X
    </button>
  </span>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },

  methods: mapActions(['removeTodo'])
}
</script>
```