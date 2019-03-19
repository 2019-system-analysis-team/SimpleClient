<template>
<body>
    <div class = "head" >
        <h2>注册</h2>
    </div>
    <div id="main">
        <p id="title">用户注册</p>
        <form action="">
            <div class="input">
                <p style="padding-left: 10px;">用户名 : <input v-model="username" type="text" name="user" id="_user"></p>
                <p style="padding-left: 15px;">密码 : <input v-model="password" type="password" name="password" id="_id"></p>
                <p style="padding-left: 20px;">电话 : <input v-model="phone" type="text" name="phone" id="_phone"></p>
                <p style="padding-left: 25px;">邮箱 : <input v-model="email" type="text" name="email" id="_email"></p><br>
                <input v-on:click="reset" type="button" value="重置" id="_reset">
                <input v-on:click="submit" type="button" value="提交">
            </div>
        </form>
    </div>
</body>
</template>

<script>
	export default {
		data() {
			return {
				username:"",
				phone: "",
				email: "",
				password:""
			};
		},
		methods:{
			submit: function () {
				//对后端提交数据检验数据是否有效
				//跳转到主页
				this.$router.push({
					path: '/', 
					name: 'mainpage',
					params: { 
						username: this.username
					},
				});
			},
			reset: function () {
				this.$data.username = "";
				this.$data.phone = "";
				this.$data.email = "";
				this.$data.password = "";
			}
	 }
	}
</script>

<style scoped>
*{
    margin: 0;
    padding: 0;
}
h2{
    margin-top: 10%;
    margin-bottom: 20px;
}
body{
    text-align: center;
}
#main{
    margin: 0 auto;
    width: 300px;
    height: 300px;
    border: 5px solid #3A3F44;
    border-radius: 10px;
    background-color:#383D42;
}
.head{
    font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
    font-size: 38px;
    line-height: 1.42857143;
    color:#757D82;
}
#title{
    margin-top: 10px;
    margin-bottom: 20px;
}
#_user{
    margin-right: 15px;
}
form span{
    margin-bottom: 20px;
    opacity: 0;
    font-size: 10px;
}
#_reset{
    margin-top: 10px;
    margin-left: 160px;
}
div>input {
    width: 60px;
    height:35px;
    background-color: #757D82;
    outline:none;
    border-radius: 15%;
    color:  #FFFFFF;
}
#login{
    margin: 0 auto;
    width: 300px;
    height: 200px;
    border: 5px solid #3A3F44;
    border-radius: 10px;
    background-color:#383D42;
}
span{
    color: red;
}
p input {
    opacity: 0.8;
}
.input{
    color: #B5B5B6;
}
.input>p{
	padding-bottom: 10px;
}
</style>
