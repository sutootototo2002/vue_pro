Vue.js 实例

构造器：

  每个Vue.js应用都是通过构造器函数Vue创建一个Vue的根实例启动的：

	  var vm = new Vue({
	
	      //todo..     
	
	  });
  
  在实例化Vue时，需要传入一个选项对象，它可以包含数据、模板、挂载元素、方法、生命周期钩子等选项。

  
组件系统：

   Vue.js组件其实都是被扩展的Vue实例。
	
	var MyComponent = Vue.extend({
	
	 //扩展项
	
	})

    // 所有的 `MyComponent` 实例都将以预定义的扩展选项被创建

    var myComponentInstance= new MyComponent()

属性与方法：

   每个Vue实例都会代理器data对象里所有的属性：

	   var data={a:1}
	   var vm = new Vue({
	       data:data
	   });
	   vm.a === data.a //true
    
       //设置属性也会影响到原始数据
       vm.a =2
       data.a //-> 2

      //反之也是
      data.a =3
      vm.a // ->3

   只有这些被代理的属性是响应的。
	
	   var data = { message: 1 }
	   var vm = new Vue({
	       el: '#example',
	       data: data
	       })
	      vm.$data === data // -> true
	      vm.$el === document.getElementById('example') // -> true
	      // $watch 是一个实例方法
	      vm.$watch('message', function (newVal, oldVal) {
	      // 这个回调将在 `vm.message`  改变后调用
	     })

   ![](http://i.imgur.com/XGG3tgQ.png)

   ![](http://i.imgur.com/HxAk1Wo.png)


  组件生命周期：

	  var vm = new Vue({
	  data: {
	    a: 1
	  },
	  created: function () {
	    // `this` 指向 vm 实例
	    console.log('a is: ' + this.a)
	  }
	})
	// -> "a is: 1"

钩子的 this 指向调用它的 Vue 实例。


![](http://i.imgur.com/HplPjPK.png)

![](http://i.imgur.com/PYg4ZrW.png)

