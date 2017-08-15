<template>
	<div>
		<div class="list_head">
			<div class="list_header">
				<div class="list_logo">
					<p>{{ title }}</p>
				</div>
				<div class="list_nav">
					<ul>
						<li @click="logClick()">登录</li>
						<li>|</li>
						<li @click="regClick()">注册</li>
					</ul>
				</div>
			</div>

			<my-dialog :is-show="isShowLogDialog" @on-close="closeDialog('isShowLogDialog')">
				<log-form></log-form>
			</my-dialog>

			<my-dialog :is-show="isShowRegDialog" @on-close="closeDialog('isShowRegDialog')">
				<reg-form></reg-form>
			</my-dialog>
		</div>
		<div class="list_main">
			<main-context></main-context>
		</div>
	</div>
</template>

<script>
	import Dialog from './dialog'
	import LogForm from './logForm'
	import RegForm from './regForm'
	import MainContext from './main'
	export default {
		data() {
			return {
				title:'TodoList',
				isShowLogDialog: false,
				isShowRegDialog: false
			}
		},
		components: {
			MyDialog : Dialog,
			LogForm,
			RegForm,
			MainContext
		},
		methods: {
			logClick() {
				this.isShowLogDialog = true
			},
			regClick() {
				this.isShowRegDialog = true
			},
			closeDialog (attr) {
				this[attr] = false
			}
		}
	}
</script>

<style>
.list_header {
	background: #000;
	height: 100px;
	width: 100%;
}
body,div,p {
	margin: 0 auto;
}
.list_logo {
	height: 100px;
	line-height: 100px;
	margin-left: 200px;
	float:left;
}
.list_logo p {
	color: #fff;
	font-size: 48px;
	font-family: "微软雅黑";
	font-weight: bold;
}

.list_nav {
	float: right;
	height: 100px;
	line-height: 100px;
	margin-right: 100px;
}
.list_nav ul {
	margin:0 auto;
}
.list_nav ul li {
	list-style: none;
	color: #fff;
	float: left;
	font-size: 20px;
	margin-right: 10px;
	cursor: pointer;
}
.list_main {
	border:2px solid #ccc;
	width: 80%;
	max-height:100%;
	margin-top: 20px;
}
</style>