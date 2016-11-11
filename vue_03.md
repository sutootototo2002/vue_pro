模板语法

 Vue.js使用了基于HTML的模板语法，允许开发者声明式的将DOM绑定至Vue实例的数据。所有Vue.js的模板都是合法的HTML,所以能被遵循规范的浏览器和HTML解析器解析。

 插值

#文本

数据绑定最常见的形式就是使用“Mustache”语法（大括号）的文本插值。

    <span>Message:{{msg}}</span>

通过 v-once指令，你也能执行一次插值，当数据改变时，插值的内容不会更新。

    <span v-once>this will never change:{{msg}}</span>

#纯HTML

   输出html需要在使用V-html指令：

     <div v-html='rawHTML'></div>

#属性

  {{}}双括号不能在HTML属性中使用，应使用V-bind指令：

     <div v-bind:id="dynamicId"></div>

  布尔值的属性也有效，如果条件被求值false的话属性会被移除：

    <button v-bind:disabled="someDynamicCondition">Button</button>

#使用JavaScript表达式

		{{ number + 1 }}
		{{ ok ? 'YES' : 'NO' }}
		{{ message.split('').reverse().join('') }}
		<div v-bind:id="'list-' + id"></div>

这些表达式会在所属 Vue 实例的数据作用域下作为 JavaScript 被解析。有个限制就是，每个绑定都只能包含单个表达式，所以下面的例子都不会生效。

#过滤器

   Vue.js 允许你自定义过滤器，被用作一些常见的文本格式化。过滤器应该被添加在 mustache 插值的尾部，由“管道符”指示：

    {{ message | capitalize }}

Vue 2.x 中，过滤器只能在 mustache 绑定中使用。为了在指令绑定中实现同样的行为，你应该使用计算属性。


#指令

  指令（Directives）是带有 v- 前缀的特殊属性。

    <p v-if="seen">Now you see me </p>

 根据表达式seen的值得真假来移除/插入<p>元素。

#参数

 有些指令可以接受参数，在指令后以冒号指明。

    <a v-bind:href="url"></a>
    <a v-on：click="doSomething">

#修饰符

    修饰符（Modifiers）是以半角句号 . 指明的特殊后缀，用于指出一个指定应该以特殊方式绑定。例如，.prevent 修饰符告诉 v-on 指令对于触发的事件调用 event.preventDefault()：

    <form v-on:submit.prevent="onSubmit"></form>

#缩写

   #v-bind 缩写

     <a v-bind:href='url'></a>


     <a :href="url"></a>

  #v-on 缩写

	<!-- 完整语法 -->
	<a v-on:click="doSomething"></a>
	<!-- 缩写 -->
	<a @click="doSomething"></a>

