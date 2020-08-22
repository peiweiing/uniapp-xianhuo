<template>
	<view class="box">
		
		<view class="divtop FX-sa">
			<text data-id='1' :class="[cid=='1'?'active w50 t-center':'w50 t-center']" @tap="select">
				手机号登录
			</text>
			<text data-id='2' :class="[cid=='2'?'active w50 t-center':'w50 t-center']" @tap="select">
				验证码登录
			</text>
		</view>
		
		<view class="input">
			<view :class="boola ? 'inpcs': 'inpcs inpcss'">
				<text>手机号：</text>
				<Iinput type="number" v-model="phone" place="请输入手机号" @blur="onphone"></Iinput>
			</view>
			<view :class="boolc ? 'inpcs': 'inpcs inpcss'" v-if="cid==1">
				<text>密码：</text>
				<Iinput type="password" v-model="pass" place="请输入密码" @blur="onpass"></Iinput>
			</view>
			<view :class="boolbs ? 'inpcs': 'inpcs inpcss'" v-if="cid==2">
				<text>验证码：</text>
				<view class="inp inpp">
					<Linput type="number" v-model="code" place="请输入验证码" @blur="oncode"></Linput>
					<button :class="cls ? 'sub':'subs'" type="primary" @click="messages">{{word}}</button>
				</view>
			</view>
		</view>
		
		<view class="butcs">
			<button @click="login">立即登录</button>
		</view>
		
		<view class="txtcs">
			<text @click="register">注册账号</text>
			<text @click="forget">找回密码</text>
		</view>
		<view class="zhezhaocs F-xy pof" v-if="tankuang">
			<view class="zhezhao">
				{{tishi}}
			</view>
		</view>
	</view>
</template>

<script>
	import Iinput from '../../components/linput.vue'
	import Linput from 'components/linput.vue'
	import App from '../../App.vue'

	export default {
		components: {
			Iinput,
			Linput
		},
		data() {
			return {
				phone:"",
				pass:"",
				code:"",//输入的验证码
				cid:'1',
				word: '获取验证码',
				isOvertime: false,
				tankuang:false,
				tishi:'',
				
				cls:false,
				boola:true,boolb:true,boolc:true,
				boolas:true,boolbs:true,boolcs:true,
			}
		},
		onLoad() {
			var that = this
			that.phone="";
			that.pass="";
			that.code="";
		},
		methods:{
			onphone(){
				let regs = /^[1][3,4,5,7,8][0-9]{9}$/;
				console.log(this.phone)
				if(!this.phone){
					this.boola=false;    
					uni.showToast({
						icon: 'none',
						title: '手机号不可为空'
					});
				}else if(!regs.test(this.phone)){
					this.boola=false;  
					uni.showToast({
						icon: 'none',
						title: '请确认手机号是否正确'
					});
				}else{
					this.boola=true;
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
			
			select(e){
				var that = this;
				console.log(e);
				that.cid=e.currentTarget.dataset.id;
				console.log(e.currentTarget.dataset.id);
				// that.phone="";
				// that.pass="";
				// that.code="";
			},
			messages(){
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
				var that =this;
				let phone = {
					'account':this.phone,
					'password':this.pass,
					'type':this.cid
				};
				console.log(this.phone)
				console.log(this.pass)
				uni.request({
					url: App.login, 
					method: 'GET',
					data: phone,
					success: (res)=>{
						console.log("请求成功")
						console.log(res)
						if(res.data.msg=="登录成功"){
							uni.setStorage({
								key:'token',
								data:res.data.data.token,
								success(){
									uni.setStorage({
										key:'user',
										data:res.data.data.token
									})
								}
							})
							that.tankuang=true;
							that.tishi = '登录成功!'
							setTimeout(function(){
								that.tankuang=false;
								uni.switchTab({
									url: '/pages/index'
								});
							},1500);
						}else{
							that.tankuang=true;
							that.tishi = '登录失败，请重新登录!'
							setTimeout(function(){
								that.tankuang=false;
							},1000)
						}
					},
					fail: (err)=>{
						console.log("请求失败")
						console.log(err)
						that.tankuang=true;
						that.tishi = '登录失败，请重新登录!'
						setTimeout(function(){
							that.tankuang=false;
						},1000)
					}
				})
			},
			register(){
				uni.navigateTo({
					url: '/pages/login/register'
				});
			},
			forget(){
				uni.navigateTo({
					url: '/pages/login/forget'
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
	.divtop{
		padding-top: 10%;
		font-size: 1rem;
	}
	.active{
		color: orangered;
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
	.inpcs .inp{
		width: 80%;
	}
	.inpcs .inpp{
		display: flex;
		align-items: center;
	}
	/* .inpcs .inpp button{
		width: 50%;
		height: 40upx;
		padding: 0;
		line-height: 40upx;
		border-radius: 40upx;
		color: #FFFFFF;
		background-color:#D096C3;
	} */
	
	.inpcss{
		border-bottom: 2px solid red;
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
	.zhezhaocs{
		background-color: rgba(200,200,200,0.4);
		width: 100%;
		height: 100%;
		top: 0;
	}
	.zhezhao{
		font-size: 1rem;
		border-radius: 20rpx;
		box-shadow: 0 0 20rpx #1A1A1A;
		background-color: #fff;
		padding: 10% 20%;
	}
</style>
