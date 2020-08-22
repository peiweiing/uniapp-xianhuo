<template>
	<view class="box">
		
		<swiper class="imgcs" :current="tabIndex" :autoplay="autoplay" :circular="circular" :interval="interval" :duration="duration" :indicator-dots="indicator" @change="tabChange">
			<swiper-item v-for="(v,i) in swiper">
				<view class="swiper-item">
					<navigator :url="v.url" style="height: inherit;">
						<image class="img" :src="v.img" mode=""></image>
					</navigator>
				</view>
			</swiper-item>
		</swiper>
		<view class="module one">
			<view class="top FY-c w50">
				<text class="rig"></text>
				<text>我要<text style="color: red;">挂牌买入/卖出</text></text>
			</view>
			<view class="end F-wrap FX-fs">
				<navigator class="w3" v-for="(v,i) in usera" :url="v.src">
					<view class="FY FY-c">
						<view class="foimg F-xy" :style="{background:v.bgc}">
							<image class="img" :src="v.img" mode=""></image>
						</view>
						<text>{{v.text}}</text>
					</view>
				</navigator>
			</view>
		</view>
		
		<!-- <view class="module two">
			<view class="top FY-c w50">
				<text class="rig"></text>
				<text>我要<text style="color: red;">摘牌买入/卖出</text></text>
			</view>
			<view class="end F-wrap FX-fs">
				<navigator class="w3" v-for="(v,i) in userb" :url="v.src">
					<view class="FY FY-c">
						<view class="foimg F-xy" :style="{background:v.bgc}">
							<image class="img" :src="v.img" mode=""></image>
						</view>
						<text>{{v.text}}</text>
					</view>
				</navigator>
			</view>
		</view> -->
		
		<view class="module two">
			<view class="top FY-c w50">
				<text class="rig"></text>
				<text>我要<text style="color: red;">限量批发</text></text>
			</view>
			<view class="end F-wrap FX-fs">
				<navigator class="w3" v-for="(v,i) in userc" :url="v.src">
					<view class="FY FY-c">
						<view class="foimg F-xy" :style="{background:v.bgc}">
							<image class="img" :src="v.img" mode=""></image>
						</view>
						<text>{{v.text}}</text>
					</view>
				</navigator>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
	            autoplay: true,
				circular: true,
				vertical: true,
				indicator:true,
	            interval: 4000,
	            duration: 1000,
				swiper:[
					{img:'../../static/banner@3x.png'},
					{img:'../../static/banner@3x.png'},
					{img:'../../static/banner@3x.png'}
				],
				usera:[
					{img:'../../static/dingdan.png',text:'我的挂单',bgc:'linear-gradient(to bottom, #f78ca0 , #fe9a8b)',src:'entrustList'},
					{img:'../../static/mairu.png',text:'挂牌买入',bgc:'linear-gradient(to bottom, #f78ca0 , #fe9a8b)',src:'entrusBuyList'},
					{img:'../../static/maichu.png',text:'挂牌卖出',bgc:'linear-gradient(to bottom, #f78ca0 , #fe9a8b)',src:'entrusSellList'},
				],
				userb:[
					{img:'../../static/kucun.png',text:'我的库存',bgc:'linear-gradient(to bottom, #f78ca0 , #fe9a8b)',src:'../user/inventoryList'},
					{img:'../../static/mairu.png',text:'摘牌买入',bgc:'linear-gradient(to bottom, #f78ca0 , #fe9a8b)',src:'entrusBuyList'},
					{img:'../../static/maichu.png',text:'摘牌卖出',bgc:'linear-gradient(to bottom, #f78ca0 , #fe9a8b)',src:'entrusSellList'},
				],
				userc:[
					{img:'../../static/gouwu.png',text:'限量批发',bgc:'linear-gradient(to bottom, #f78ca0 , #fe9a8b)',src:'wholesaleList'},
				],
			}
		},
		methods: {
			tabChange(e) {
				this.tabIndex = e.detail.current;
				// console.log(e.detail.current)
			}
		}
	}
</script>

<style>
	.box{
		min-height: calc(100vh);
		background-color: rgb(245,245,245);
	}
	.imgcs .swiper-item{
		height: inherit;
	}
	.imgcs .img{
		width: 100%;height: 100%;
	}
	.module{
		margin: 2% 0;
		background-color: #fff;
	}
	.module .rig{
		width: 14rpx;
		margin-right: 10rpx;
		border-top: 50rpx solid orangered;
	}
	.one{
		padding-bottom: 4%;
	}
	.module .top{
		padding: 4%;
		font-size: 1rem;
	}
	.module .end{
		padding: 4%;
	}
	.module .end text{
		font-size: 0.8rem;
	}
	.module .foimg{
		margin-bottom: 5%;
		padding: 12%;
		border-radius: 50%;
	}
	.module .foimg .img{
		width: 1.3rem;
		height: 1.3rem;
		margin: 0;
	}
</style>
