<template>
	<view class="box">
		<view class="input">
			<!-- <view :class="dool ? 'inpcs': 'inpcs inpcss'">
				<text>手机号：</text>
				<input class="inp" type="text" v-model="phone" placeholder="请输入手机号码" @blur="onphone()"/>
			</view> -->
			<!-- <view class="inpcs">
				<text>验证码：</text>
				<view class="inp inpp">
					<input type="password" value="" placeholder="请输入验证码" />
					<button class="sub" type="primary" @click="sendMessage">{{word}}</button>
				</view>
			</view> -->
			<!-- <view class="inpcs">
				<text>新密码：</text>
				<input class="inp" type="password" value="" placeholder="密码不少于6位数" />
			</view> -->
			
			<view :class="boola ? 'inpcs': 'inpcs inpcss'">
				<text>手机号：</text>
				<Linput type="number" v-model="phone" place="请输入手机号" @blur="onphone"></Linput>
			</view>
			<view :class="boolb ? 'inpcs': 'inpcs inpcss'">
				<text>验证码：</text>
				<view class="inp inpp">
					<Linput type="number" v-model="code" place="请输入验证码" @blur="oncode"></Linput>
					<button :class="cls ? 'sub':'subs'" type="primary" @click="message">{{word}}</button>
				</view>
			</view>
			<view :class="boolc ? 'inpcs': 'inpcs inpcss'">
				<text>新密码：</text>
				<Linput type="password" v-model="pass" place="请输入密码" @blur="onpass"></Linput>
			</view>
		</view>
		
		<view class="butcs">
			<button>找回密码</button>
		</view>
		
		<view class="txtcs">
			<text @click="login">立即登录</text>
			<text @click="register">立即注册</text>
		</view>
			
	</view>
</template>

<script>
	import Linput from '../../components/linput.vue'

	export default {
		components: {
			Linput
		},
		data() {
			return {
				phone:"",//注册页面用户名//判断输入框的值是否符合用户名规则
				pass:"",//密码
				code:"",//输入的验证码
				word: '获取验证码',
				isOvertime: false,
				
				cls:false,
				boola:true,boolb:true,boolc:true
			};
		},
		methods: {
			
			onphone(){
				let regs = /^[1][3,4,5,7,8][0-9]{9}$/;
				console.log(this.phone)
				if(!this.phone){
					this.boola=false;   
					this.cls=false;  
					uni.showToast({
						icon: 'none',
						title: '手机号不可为空'
					});
				}else if(!regs.test(this.phone)){
					this.boola=false; 
					this.cls=false; 
					uni.showToast({
						icon: 'none',
						title: '请确认手机号是否正确'
					});
				}else{
					this.boola=true;
					this.cls=true;
				}
			},
			oncode(){
				if(!this.code){
					this.boolb=false;
					uni.showToast({
						icon: 'none',
						title: '验证码不可为空'
					});
				}else{
					this.boolb=true;  
				}
			},
			onpass(){
				if(!this.pass){
					this.boolc=false;
					uni.showToast({
						icon: 'none',
						title: '密码不可为空'
					});
				}else{
					this.boolc=true;  
				}
			},
			
			message(){
				console.log('点击了')
				let regs = /^[1][3,4,5,7,8][0-9]{9}$/;
				let that = this,
					time = 60;
				if(this.phone!=''&&regs.test(this.phone)){
					console.log('执行')
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
			},
			
			login(){
				uni.navigateTo({
					url: '/pages/login/login'
				});
			},
			register(){
				uni.navigateTo({
					url: '/pages/login/register'
				});
			},
			
			
		}
	}
</script>

<style>
	.box{
		min-height: calc(100vh);
		background: url(../../static/login_bg@3x.png) no-repeat fixed bottom;
		background-size: 100% 40%;
	}
	.input{
		width: 100%;
		padding: 10% 0;
	}
	.inpcs{
		font-size: 0.8rem;
		padding: 2%;
		margin: 6%;
		display: flex;
		align-items: center;
		justify-content: flex-start;
		border-radius: 50upx;
		border-bottom: 6upx solid #D096C3;
		box-shadow: 0 4upx 20upx #d096c3;
	}
	.inpcs text{
		width: 20%;
		text-align: center;
	}
	.inpcss{
		border-bottom: 2px solid red;
	}
	.inpcs .inp{
		width: 80%;
	}
	.inpcs .inpp{
		display: flex;
		align-items: center;
	}
	
	.sub{
		padding: 0;
		width: 70%;
		height: 1.4rem;
		line-height: 1.4rem;
		border-radius: 2rem;
		color: #FFFFFF;
		background-color:#D096C3;
	}
	.subs{
		padding: 0;
		width: 70%;
		height: 1.4rem;
		line-height: 1.4rem;
		border-radius: 2rem;
		color: #FFFFFF;
		background-color:#ccc;
	}
	.butcs button{
		margin: 0 6%;
		border-radius: 80upx;
		color: #FFFFFF;
		background-color:#ccc;
		background-image:linear-gradient(left,#ead6ee,#ef96c5);;
	}
	.txtcs{
		margin-top:10%;
		display: flex;
		justify-content: space-around;
		align-items: center;
	}
</style>
