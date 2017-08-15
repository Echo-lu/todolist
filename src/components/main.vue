<template>
	<div>
		<div class="main_wrap">
			<h1>TodoList</h1>
		</div>
		<div class="main_add">
			<span>我的计划：</span>
			<input type="text" v-model="plan" placeholder="添加计划" ><br>
			<span>计划时间：</span>
			<input type="text" v-model="plantime" placeholder="enter添加" @keyup.enter="addlist">
		</div>
		<div class="main_list">
			<ol>
				<li v-for="(item,index) in list" >{{item.name}}&nbsp;&nbsp;-&nbsp;&nbsp;{{item.time}}
				<span class="undo" v-show="!item.isShow" @click="undolist(index)">取消计划</span>
				<span class="isfinish" v-show="!item.isShow" @click="finish(item)">已完成</span>
				<span class="finish" v-show="item.isShow">已完成</span></li>

			</ol>
		</div>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				plan: '',
				plantime: '',
				list: [
					{
						name: '运动',
						time: '07:00',
						isShow: true
					},
					{
						name: '早餐',
						time: '08:00',
						isShow: false
					},
					{
						name: '工作',
						time: '09:00',
						isShow: false
					}
				]
				
			}
		},
		methods: {
			addlist() {
				if(this.plan.length != 0 && /^(20|21|22|23|[0-1]\d):[0-5]\d$/.test(this.plantime)) {
					this.list.push({
					name: this.plan,
					time: this.plantime,
					isShow: false
				})
				}else if(this.plan.length == 0) {
					alert("计划不为空")
				}
				else {
					alert("时间格式不对！")
				}
				
				this.plan = ''
				this.plantime= ''
				
			},
			finish(list) {
				list.isShow = true
			},
			undolist(index) {
				 this.list.splice(index, 1);
			}
		}
	}
</script>

<style>
.main_wrap {
	margin: 0 auto;
}
.main_wrap h1{
	text-align: center;
}
.main_add {
	width: 100%;
	text-align: center;
}
.main_add span {
	font-family: "微软雅黑";
	font-size: 20px;
	font-weight: bold;
}
.main_add input {
	width:40%;
	height: 30px;
	margin-bottom: 20px;
	border-radius: 5px;
	border:1px solid #999;
	font-size: 16px;
	padding-left: 10px;

}
.main_list {
	margin-left: 100px;
}
.main_list ol li {
	font-size: 20px;
	margin-bottom: 10px;
}
.main_list ol li:hover {

	color:orange;
}
.main_list ol li .undo,.main_list ol li .isfinish {
	margin-left: 10px;
	color:#00f;
	font-size: 16px;
	cursor: pointer;
}
.finish {
	margin-left: 10px;
	color:#c00;
	font-size: 16px;
}
</style>