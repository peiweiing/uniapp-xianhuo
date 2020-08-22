<template>
	<view class="box">
		<view class="FY-fs logocs">
			<!-- <image class="logo" src="../../static/logo.png" mode=""></image> -->
			<view class="FY FX-sa" style="margin-top: 8%;">
				<text>name</text>
				<text>当前权益
					<text style="font-size: 1rem;">{{2145}}</text>
				元</text>
			</view>
		</view>
		<!-- <view class="user">
			<view class="FX-sb div">
				<view class="FY-c w30">
					<image class="img" src="../../static/logo.png" mode=""></image>
					<text>我的名片</text>
				</view>
				<text>></text>
			</view>
			<view class="FX-sa div">
				<navigator v-for="(v,i) in usertop" :url="v.src">
					<view class="FY FY-c">
						<image class="imgtop" :src="v.img" mode=""></image>
						<text>{{v.text}}</text>
					</view>
				</navigator>
			</view>
		</view> -->
		<view class="user one FX-sa">
			<view class="onel w40 FY FY-c">
				<view class="FY FY-c">
					<text>
						<text style="font-size: 1rem;">35.20</text>元
					</text>
					<text>可用资金</text>
				</view>
				<button class="w70">入金</button>
			</view>
			<view class="cent">
				
			</view>
			<view class="oner w40 FY FY-c">
				<view class="FY FY-c">
					<text>
						<text style="font-size: 1rem;">35.20</text>元
					</text>
					<text>可出资金</text>
				</view>
				<button class="w70">出金</button>
			</view>
		</view>
		
		<view class="user two">
			<view class="FX-sb div">
				<view class="FY-c w30">
					<text>银行卡管理</text>
				</view>
				<text></text>
			</view>
			<view>
				<navigator v-for="(v,i) in usera" :url="v.src">
					<Uuser :imgsrc="v.img" :text="v.text"></Uuser>
				</navigator>
			</view>
		</view>
		
		<view class="user three FX-sb">
			<navigator class="nav w40" v-for="(v,i) in userb" :url="v.src" :style="{background:v.bgc}">
				<!-- <Uuser :imgsrc="v.img" :text="v.text"></Uuser> -->
				<view class="FX-sa FY-c">
					<view class="thimg F-xy w20">
						<image class="img" :src="v.img" mode=""></image>	
					</view>
					<text class="w40">{{v.text}}</text>
				</view>
			</navigator>
		</view>
		
		<view class="user four">
			<view class="FX-sb div">
				<view class="FY-c w30">
					<text>我要提货</text>
				</view>
				<text></text>
			</view>
			<view class="F-wrap FX-fs">
				<navigator class="w30" v-for="(v,i) in userc" :url="v.src">
					<!-- <Uuser :imgsrc="v.img" :text="v.text"></Uuser> -->
					<view class="FY FY-c">
						<view class="foimg F-xy" :style="{background:v.bgc}">
							<image class="img" :src="v.img" mode=""></image>
						</view>
						<text class="txt">{{v.text}}</text>
					</view>
				</navigator>
			</view>
		</view>
	</view>
</template>

<script>
	import Uuser from '../../components/user/uuser.vue'

	export default {
		components: {
			Uuser
		},
		data() {
			return {
				usertop:[
					{img:'../../static/logo.png',text:'我的发布',src:''},
					{img:'../../static/logo.png',text:'我的发布',src:''},
					{img:'../../static/logo.png',text:'我的发布',src:''},
					{img:'../../static/logo.png',text:'我的发布',src:''},
				],
				usera:[
					{img:'../../static/logo.png',text:'入金记录',src:'bookLog'},
					{img:'../../static/logo.png',text:'出金记录',src:'chargeOffLog'},
					{img:'../../static/logo.png',text:'修改资金密码',src:''},
				],
				userb:[
					{img:'../../static/jiaoyi.png',text:'交易记录',bgc:'linear-gradient(to bottom, rgb(249,124,138) , rgb(244,89,108))',src:''},
					{img:'../../static/yaoqing.png',text:'邀请拼购',bgc:'linear-gradient(to top, rgb(252,113,106) , rgb(244,117,110))',src:''},
				],
				userc:[
					{img:'../../static/dizhi.png',text:'地址管理',bgc:'linear-gradient(to bottom, rgb(255,70,4) , rgb(254,141,99))',src:''},
					{img:'../../static/kucun.png',text:'库存提货',bgc:'linear-gradient(to bottom, rgb(255,70,4) , rgb(254,141,99))',src:''},
				],
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	.box{
		min-height: calc(100vh);
		background-color: rgb(245,245,245);
	}
	.user{
		margin: 0 4%;
		margin-top: 4%;
		padding: 2%;
		background-color: #fff;
		border-radius: 20rpx;
	}
	.div{
		padding: 4% 2%;
	}
	.logocs{
		color: #fff;
		padding: 0 6%;
		background: url(../../static/bgc.jpg) no-repeat;
		background-size: 100% 100%;
		min-height: calc(20vh);
	}
	.logo{
		width: 4rem;
		height: 4rem;
		border-radius: 50%;
		margin-right: 5%;
	}
	.img{
		width: 1rem;
		height: 1rem;
		margin-right: 8%;
	}
	.imgtop{
		width: 1.5rem;
		height: 1.5rem;
		margin-bottom: 10%;
	}
	.one{
		margin-top: -12%;
		padding: 4% 0;
	}
	.one button{
		margin-top: 5%;
		height: 1.6rem;
		line-height: 1.6rem;
		border-radius: 10rpx;
		background-color: #fff;
	}
	.one .cent{
		border: 1px solid #efeff4;
	}
	.onel button{
		color: orangered;
		border: 1px solid orangered;
	}
	.oner button{
		color: #fff;
		background-color: orangered;
	}
	.three{
		padding: 0;
		background-color: rgb(245,245,245);
	}
	.three .nav{
		color: #fff;
		background-color: #007AFF;
		padding: 4%;
		border-radius: 10rpx;
	}
	.three .thimg{
		padding: 8%;
		background-color: #fff;
		border-radius: 50%;
	}
	.three .thimg .img{
		width: 1.3rem;
		height: 1.3rem;
		margin: 0;
	}
	.four{
		padding-bottom: 4%;
	}
	.four .foimg{
		padding: 10%;
		border-radius: 50%;
	}
	.four .foimg .img{
		width: 1.3rem;
		height: 1.3rem;
		margin: 0;
	}
	.txt{
		margin-top: 5%;
	}
</style>
