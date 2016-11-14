计算属性

难以维护的：

	<div id="example">
	  {{ message.split('').reverse().join('') }}
	</div>

#基础例子

##计算属性

	<div id="example">
	  <p>Original message: "{{ message }}"</p>
	  <p>Computed reversed message: "{{ reversedMessage }}"</p>
	</div>

	var vm = new Vue({
	  el: '#example',
	  data: {
	    message: 'Hello'
	  },
	  computed: {
	    // a computed getter
	    reversedMessage: function () {
	      // `this` points to the vm instance
	      return this.message.split('').reverse().join('')
	    }
	  }
	})

#计算缓存 VS Methods

不同的是计算属性是基于它的依赖缓存。计算属性只有在它的相关依赖发生改变时才会重新取值。这就意味着只要 message 没有发生改变，多次访问 reversedMessage 计算属性会立即返回之前的计算结果，而不必再次执行函数。

#计算缓存 VS Watched Property
	var vm = new Vue({
	  el: '#demo',
	  data: {
	    firstName: 'Foo',
	    lastName: 'Bar',
	    fullName: 'Foo Bar'
	  },
	  watch: {
	    firstName: function (val) {
	      this.fullName = val + ' ' + this.lastName
	    },
	    lastName: function (val) {
	      this.fullName = this.firstName + ' ' + val
	    }
	  }
	})


这种方式更好：

	var vm = new Vue({
	  el: '#demo',
	  data: {
	    firstName: 'Foo',
	    lastName: 'Bar'
	  },
	  computed: {
	    fullName: function () {
	      return this.firstName + ' ' + this.lastName
	    }
	  }
	})

#计算 setter

	// ...
	computed: {
	  fullName: {
	    // getter
	    get: function () {
	      return this.firstName + ' ' + this.lastName
	    },
	    // setter
	    set: function (newValue) {
	      var names = newValue.split(' ')
	      this.firstName = names[0]
	      this.lastName = names[names.length - 1]
	    }
	  }
	}
	// ...

##观察Watchers

	<div id="watch-example">
	  <p>
	    Ask a yes/no question:
	    <input v-model="question">
	  </p>
	  <p>{{ answer }}</p>
	</div>