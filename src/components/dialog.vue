<template>
	<div>
		<div class="dialog_wrap" v-if="isShow">
			
			<div class="dialog_cover" @click="closeMyself">
			</div>
			<div class="dialog_content">
				<p class="dialog_close" @click="closeMyself">X</p>
				<slot>empty</slot>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		props: {
			isShow: {
				type:Boolean,
				default: false
			}
		},
		methods: {
			closeMyself() {
				this.$emit('on-close')
			}
		}
	}
</script>

<style>
.dialog_wrap {
	position: fixed;
	width: 100%;
	height: 100%;
}
.dialog_cover {
	background: #000;
	opacity: .3;
	position: fixed;
	z-index: 5;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
}

.dialog_content {
	width: 50%;
	max-height: 50%;
	position: fixed;
	z-index: 10;
	background: #fff;
	overflow: hidden;
	top:200px;
	left: 25%;
	border:2px solid #464068;
	padding: 2px;
	line-height: 1.6;	
}

.dialog_close {
	position: absolute;
	right: 10px;
	top:5px;
	width: 20px;
	height: 20px;
	text-align: center;
	cursor: pointer;
}
.dialog_close:hover {
	color: #c00;
}

</style>