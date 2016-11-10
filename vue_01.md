Vue.js 学习笔记

1、数据驱动开发型框架--Vue.js

2、学习基础和学习方法。

--什么是Vue.js?
  
	  1、客户端JavaScript的框架
	
	  2、用于数据驱动的现代web开发

      3、实现了MVVM思想

常见的界面驱动：数据驱动 VS 界面驱动

     例子：如果有一个登陆框，我们应该怎么来做。
    
     如果实现？
     
       用dom操作的方式：
     
     界面驱动：

       有设计稿切成html,然后在html的要求下添加逻辑。

![](http://i.imgur.com/2Ogweug.png)


     

     
 数据驱动：
    
   ![](http://i.imgur.com/3TtbkXz.png)

   
   是双向数据绑定的：

     从View侧看，ViewModel中的DOM Listeners工具会帮我们监测页面上DOM元素的变化，如果有变化，则更改Model中的数据；

     从Model侧看，当我们更新Model中的数据时，Data Bindings工具会帮我们更新页面中的DOM元素。


     只关心逻辑，不需要关心在哪里用。界面与逻辑分离，解耦。
  
     

第一个小例子：
	
	   <!DOCTYPE html>
	<html>
	<head>
	    <meta http-equiv=”Content-Type” content=”text/html;charset=urf-8”>
	    <title>Vue.js学习</title>
	    <script type="text/javascript" src="js/vue.js"></script>
	</head>
	<body>
	   <div id="app">
	       {{message}}
	   </div>
	<script type="text/javascript">
	    var app = new Vue({
	        el:"#app",
	        data:{
	            message:'hello Vue!'
	        }
	    })
	</script>
	</body>
	</html>

打开控制台：

  你可以修改model层的数据，view也可以瞬间改变。

![](http://i.imgur.com/SMxM1Kd.png)


第二个小例子：
	
	<!DOCTYPE html>
	<html>
	<head>
	    <meta http-equiv=”Content-Type” content=”text/html;charset=urf-8”>
	    <title>View层改变</title>
	    <script type="text/javascript" src="js/vue.js"></script>
	
	</head>
	<body>
	   <div id="app-2">
	       <span v-bind:title="message">
	           sususususu,i love you !
	       </span>
	   </div>
	<script type="text/javascript">
	    var app2 = new Vue({
	        el:'#app-2',
	        data:{
	            message:'你好'+new Date()
	        }
	    })
	</script>
	</body>
	</html>

控制台修改<span>元素的标题
![](http://i.imgur.com/pHd6M1k.png)


第三个例子：
	
	<!DOCTYPE html>
	<html>
	<head>
	    <meta http-equiv=”Content-Type” content=”text/html;charset=urf-8”>
	    <title>View层改变</title>
	    <script type="text/javascript" src="js/vue.js"></script>
	
	</head>
	<body>
	   <div id="app-3">
	      <p v-if="seen">你看见我了吗</p>
	   </div>
	<script type="text/javascript">
	    var app3 = new Vue({
	        el:'#app-3',
	        data:{
	            seen:true
	        }
	    })
	</script>
	</body>
	</html>

控制台：

之前：

![](http://i.imgur.com/h8eWhSu.png)

之后：#app3 中的内容不需要刷新，就自动消失了。

![](http://i.imgur.com/u8G14tj.png)
![](http://i.imgur.com/NzJM9Lz.png)


第四个例子：

	<!DOCTYPE html>
	<html>
	<head>
	    <meta http-equiv=”Content-Type” content=”text/html;charset=urf-8”>
	    <title>View层改变</title>
	    <script type="text/javascript" src="js/vue.js"></script>
	
	</head>
	<body>
	   <div id="app-4">
	      <ul>
	          <li v-for="todo in todos">
	              {{todo.text}}
	          </li>
	      </ul>
	   </div>
	<script type="text/javascript">
	    var app4 = new Vue({
	        el:'#app-4',
	        data:{
	            todos:[
	                {text:'suxiaoyan'},
	                {text:'floweryan'},
	                {text:'pangsuman'}
	            ]
	        }
	    })
	</script>
	</body>
	</html>

![](http://i.imgur.com/H7Bxmle.png)

   插入数组：

    app4.todos.push({ text: 'New item' })

![](http://i.imgur.com/rQAOqby.png)

![](http://i.imgur.com/L8oIHsj.png)


第五个例子：表单的添加删除

	<!DOCTYPE html>
	<html xmlns:v-on="http://www.w3.org/1999/xhtml">
	<head>
	    <meta http-equiv=”Content-Type” content=”text/html;charset=urf-8”>
	    <title>View层改变</title>
	    <script type="text/javascript" src="js/vue.js"></script>
	
	</head>
	<body>
	<div id="app-5">
	   <ul>
	       <li v-for="todo in todos">
	           {{ todo.text }}
	       </li>
	   </ul>
	    <button v-on:click="add">add</button>
	    <button v-on:click="plus">plus</button>
	</div>
	
	<script type="text/javascript">
	    var app5 = new Vue({
	        el: '#app-5',
	        data: {
	            todos: [
	                { text: 'Learn JavaScript' },
	                { text: 'Learn Vue' },
	                { text: 'Build something awesome' }
	            ]
	        },
	        methods: {
	            add: function () {
	                this.todos.push({text:"susu"});
	            },
	            plus:function(){
	                this.todos.pop();
	            }
	        }
	    })
	
	</script>
	</body>
	</html>

![](http://i.imgur.com/HeqtzM1.png)

第六个例子：model

	<!DOCTYPE html>
	<html>
	<head>
	    <meta http-equiv=”Content-Type” content=”text/html;charset=urf-8”>
	    <title>v-model</title>
	    <script type="text/javascript" src="js/vue.js"></script>
	</head>
	<body>
	<div id="app-6">
	    <p>{{ message }}</p>
	    <input v-model="message">
	</div>
	  <script type="text/javascript">
	      var app6 = new Vue({
	          el: '#app-6',
	          data: {
	              message: 'Hello Vue!'
	          }
	      });
	  </script>
	</body>
	</html>


