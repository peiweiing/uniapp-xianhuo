<template>
	<view class="inpp">
		<input class="getinp" :type="type" :placeholder="place" @input="onInput" @blur="onblur"/>
		<button class="sub" type="primary" @click="message">{{word}}</button>
	</view>
</template>

<script>
	export default {
		props: {
			/**类型**/
			type: String,
			//*默认显示**/
			place: String
		},
		model: {
			prop: 'value',
			event: 'input'
		},
		data() {
			return {
				word: '发送验证码',
				isOvertime: false,
				getinp:''
			};
		},
		methods:{
			onblur() {
				this.$emit('blur')
			},
			onInput(e) {
				this.$emit('input', e.target.value)
				this.getinp=e.target.value
			},
			message() {
				if(this.isOvertime){
					return false;
				}
				let that = this,
					time = 60;
				var getinp = document.querySelector('.getinp').value
				var sendTimer = setInterval(function(){
					var sub=document.getElementsByClassName('sub')[0];
					that.isOvertime = true;
					time--;
					that.word = time+'S后重试';
					sub.style.backgroundColor='#ccc';
					if(time < 0){
						that.isOvertime = false;
						clearInterval(sendTimer);
						that.word = "获取验证码";
						sub.style.backgroundColor='#D096C3';
						sub.style.color='#fff';
					}
				},1000)
			}
			
		}
	}
</script>

<style>
	.inpp{
		display: flex;
	}
	.sub{
		width: 50%;
		height: 40upx;
		padding: 0;
		line-height: 40upx;
		border-radius: 40upx;
		color: #FFFFFF;
		background-color:#D096C3;
	}
</style>
