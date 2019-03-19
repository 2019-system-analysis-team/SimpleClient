<template>
	<div>
		<a v-on:click="loginOrMod" href="javascript:void(0);">{{username}}</a>
		<a v-on:click="registerOrOut" href="javascript:void(0);">{{status}}</a>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				 username:"",
				 isLogin:false,
				 status: ""
			};
		},
		created: function () { 
			//在created阶段初始化
			this.getEventData();
		},
		methods: {
			getEventData:function() {
				let routerParams = this.$route.params.username;
				if(routerParams == null){
					this.username = "登录";
					this.status = "注册";
					this.isLogin = false;
					//可以对用户的token进行检验是否超出登出时间
				}else{
					this.username = routerParams;
					this.isLogin = true;
					this.status = "退出登录";
				}
			},
			loginOrMod: function () {
				if(this.isLogin){							
					this.$router.push({
							path: '/userinfomodify', 
							name: 'userinfomodify',
							params: { 
									username: this.username
							}
					});
				}
				else{
					this.$router.push({
							path: '/userlogin'
					});
				}
			},
			registerOrOut: function () {
				if(this.isLogin){	
					this.isLogin = false;
					this.username = "登录";
					this.status = "注册";
					//退出登录，将用户token失效
				}else{
					//注册
					this.$router.push({
						path: '/userregister'
					});
				}
			}
		}
	}
</script>

<style>
</style>
