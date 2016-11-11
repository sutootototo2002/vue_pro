计算属性

难以维护的：

	<div id="example">
	  {{ message.split('').reverse().join('') }}
	</div>

#基础例子

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