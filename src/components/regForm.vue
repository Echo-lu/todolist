<template>
	<div>
		<div class="log_form">
			<p class="warn"> {{errorText}}</p>

			<div class="log_form_name">
				<span>用户名：</span>
				<input type="text" placeholder="请输入用户名" v-model="username">
				<span class="g_form_error">{{ userErrors.errorText }}</span>
			</div>

			<div class="log_form_pwd">
				<span>密&nbsp;&nbsp;&nbsp;码：</span>
				<input type="password" placeholder="请输入密码" v-model="password">
				<span class="g_form_error">{{ passwordErrors.errorText }}</span>
			</div>
			
			<div class="log_form_submit">
				<input type="submit" @click="onReg" value="注册">
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
		computed: {
			userErrors() {
				let status,errorText
				if(!/@/g.test(this.username)) {
					status = false
					errorText = "没有包含@"
				}else {
					status = true
					errorText = ""
				}
				if(!this.userFlag) {
					errorText=""
					this.userFlag = true
				}
				return {
					status,
					errorText
				}
			},
			passwordErrors() {
				let status,errorText
				if(!/^\w{1,6}$/g.test(this.password)){
					status = false
					errorText = "密码不是1-6位"
				}else {
					status = true
					errorText = ''
				}
				if(!this.passwordFlag ) {
					errorText=""
					this.passwordFlag = true
				}
				return {
					status,
					errorText
				}
			}
		},
		methods: {
			onReg() {
				if(!this.userErrors.status || !this.passwordErrors.status) {
					alert('Sorry,It is fail to Register!')
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
.g_form_error {
	color:#c00;
}
.warn {
	color:#c00;
	margin-bottom: 20px;
	margin-left: 100px;
}
</style>