<template>
	<router-view></router-view>
</template>

<script>
	// import Home from './views/Home.vue';
	// export default{
	// 	components: {
	// 		Home,
	// 	}
	// }
	// let em = new Vue({
	// 	el: '#app',
	// 	created() {
	// 		console.log('建立');
	// 	}
	// })
	import Cookies from 'js-cookie';
	export default {
		name: 'app',
		created() {
			console.log('开始运行程序');
			let testData = [
				{'区间':'江安-华西','日期':'2021-05-10','时间':'15:20'},
				{'区间':'江安-华西','日期':'2021-05-15','时间':'08:25'}
			]
			this.$store.commit('updateTicketsStatus',testData);
			let cs = Cookies.get('name');
			if(cs){
				this.$store.commit('updateStatus',true);
			}
		}
	}
</script>

<style lang="scss">
	body{
		margin: 0;
		padding: 0;
		
	}
	input::-webkit-input-placeholder{
		font-family: 'Courier New', '楷体' !important;
	}
	button{
		font-family: 'Courier New', '楷体';
		font-size: 16px;
		line-height: 100%;
	}
#app {
  // font-family: Avenir, Helvetica, Arial, sans-serif;
  font-family: 'Courier New', '楷体';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

</style>
