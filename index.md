<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<script src="js/vue.js" type="text/javascript" charset="UTF-8"></script>
		<title>猜数字游戏</title>
	</head>
	<body>
		<div id="app-5">
		  <p>{{ message }}</p>
		  <my-game></my-game>
		  
		</div>

	<script type="text/javascript">
		Vue.component("my-game",{
		   data:function(){
			return {
			 randomNum:0,
			 myInput:0,
			 result:""
			}
         },
		template:`
		<div>
		 <input type="text" v-model.number="myInput"/>
		 <br>
		 <p>{{result}}</p>
		</div>
	   `,
	   beforeMount: function () {
		  //创建一个100以内的随机的整数
		  var num = Math.floor(Math.random()*100);
		  console.log(num);
		  this.randomNum = num;
		  },
		   //当数据改变时执行的操作
		   watch:{
			myInput:function(){
			 if(this.myInput==this.randomNum){
			  this.result = "恭喜：猜对了";
			 }else if(this.myInput>this.randomNum){
			  this.result = "啊哦！猜大了";
			 }else{
			  this.result = "啊哦！猜小了";
			 }
			}
		   }
		  })
		  
		var app5 = new Vue({
		  el: '#app-5',
		  data: {
			message: 'Hello Vue.js!',
			}
		  })
	</script>
		
	</body>
</html>
