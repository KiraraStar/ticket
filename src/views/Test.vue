<template>
	<div>
		<p>test</p>
		<button @click="send"></button>
	</div>
</template>

<script>
	export default{
		data(){
			return {
				path: '/',
				socket: {},
			}
			
		},
		mounted(){
			this.init();
		},
		methodd: {
			init() {
				if(typeof(WebSocket) === "undefined"){
					alert("您的浏览器不支持socket")
				}else{
					// 实例化socket
					this.socket = new WebSocket(this.path)
					// 监听socket连接
					this.socket.onopen = this.open
					// 监听socket错误信息
					this.socket.onerror = this.error
					// 监听socket消息
					this.socket.onmessage = this.getMessage
				}
			},
			open: function () {
				console.log("socket连接成功")
			},
			error: function () {
				console.log("连接错误")
			},
			getMessage: function (msg) {
				console.log(msg.data)
			},
			send: function () {
				this.socket.send('data');
			},
			close: function () {
				console.log("socket已经关闭")
			}
		},
		unmounted() {
			this.socket.onclose = this.close;
		}
	}
</script>

<style>
</style>
