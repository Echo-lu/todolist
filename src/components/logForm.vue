<template>
	<div>
		<div class="log_form">
			<p class="warn"> {{errorText}}</p>
			<div class="log_form_name">
				<span>用户名：</span>
				<input type="text" placeholder="请输入用户名" v-model="username">
			</div>

			<div class="log_form_pwd">
				<span>密&nbsp;&nbsp;&nbsp;码：</span>
				<input type="password" placeholder="请输入密码" v-model="password">
			</div>
			
			<div class="log_form_submit">
				<input type="submit" @click="onLog" value="登录">
			</div>
		</div>
	</div>
</template>
<script>
	export default {
		data() {
			return {
				username: '',
				password: '',
				errorText: ''
			}
		},
		methods: {
			onLog() {
				if(this.username.length == 0 || !this.password.length == 0) {
					alert('Sorry,It is fail to Login!')
					this.errorText = "用户名或密码错误！"
				}else {
					this.errorText = ""
					
				}
			}
		}
	}
</script>
<style>
.log_form {
	margin-top: 40px;
}
.log_form_name,.log_form_pwd {
	margin-bottom: 20px;
	margin-left: 20px;
}
.log_form_name input,.log_form_pwd input{
	width:250px;
	height: 30px;
	padding-left: 10px; 
}
.log_form_submit input{
	margin-left: 100px;
	background: #4fc08d;
	border:2px #4fc08d solid;
	width: 60px;
	height: 30px;
	margin-bottom: 20px;
	color:#fff;
}	
.log_form_submit input:hover {
	background: #4fc02d;
}
</style>