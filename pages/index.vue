<template>
    <view class="box">
		<view class="bgccs">
			<view>
				<!-- 首页 -->
			</view>
		</view>
		<swiper class="swiper" :current="tabIndex" :autoplay="autoplay" :circular="circular" :interval="interval" :duration="duration" @change="tabChange">
			<swiper-item>
				<view class="swiper-item">
					<image src="../static/banner@3x.png" mode=""></image>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item">
					<image src="../static/banner@3x.png" mode=""></image>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item">
					<image src="../static/banner@3x.png" mode=""></image>
				</view>
			</swiper-item>
		</swiper>
		<view class="moduleone FX-sb F-wrap">
			<navigator class="w4" v-for="(v,i) in moduleone" :url="v.url">
				<view class="module FY FY-c">
					<image class="img" :src="v.src" mode=""></image>
					<text>{{v.text}}</text>
				</view>
			</navigator>
		</view>
		<view class="moduletwo">
			<view class="FX-sb twotop">
				<view>
					热门标题
				</view>
				<view>
					<text>更多</text>
					<text>></text>
				</view>
			</view>
			<view class="FX-sb F-wrap"> 
				<navigator class="" v-for="(v,i) in moduletwo" :url="v.url">
					<view class="module">
						<image class="img" :src="v.src" mode=""></image>
						<view class="text">
							<text>{{v.title}}</text>
							<view class="">
								<text>{{v.price}}</text>
								<!-- <text>教学</text> -->
							</view>
						</view>
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
	            interval: 4000,
	            duration: 1000,
				// leftcs:"1rem",
				// rightcs:"1rem",
				tabIndex:0,
				
				moduleone:[
					{src:'../static/logo.png',text:'小学',url:'',},
					{src:'../static/logo.png',text:'小学',url:'',},
					{src:'../static/logo.png',text:'小学',url:'',},
					{src:'../static/logo.png',text:'小学',url:'',},
					{src:'../static/logo.png',text:'小学',url:'',},
				],
				moduletwo:[
					{src:'../static/logo.png',title:'标题内容标题',price:'￥99',url:'',},
					{src:'../static/logo.png',title:'标题内容标题',price:'￥99',url:'',},
					{src:'../static/logo.png',title:'标题内容标题',price:'￥99',url:'',},
					{src:'../static/logo.png',title:'标题内容标题',price:'￥99',url:'',},
				]
	        }
	    },
		onLoad() {
		
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
		background-color: #F1F1F1;
		min-height: calc(100vh);
		padding-bottom: 5%;
	}
	.bgccs{
		background: url(../static/tt02.png) no-repeat 100% 100%;
		background-size: 100% 100%;
		min-height: calc(20vh);
	}
	.swiper{
		padding: 0 5%;
		margin-top: calc(-10vh);
	}
	.swiper-item image{
		border-radius: 20rpx;
		margin: 0 2%;
	}
	
	.moduleone{
		margin: 5%;
		padding: 1rem 0;
		background-color: #fff;
		border-radius: 1rem;
	}
	.moduleone .module{
		padding: 0.5rem;
	}
	.moduleone .img{
		width: 2rem;
		height: 2rem;
	}
	
	.moduletwo .img{
		width: 5rem;
		height: 5rem;
	}
	
	.moduletwo{
		margin: 5%;
		padding: 1rem;
		background-color: #fff;
		border-radius: 1rem;
	}
	.moduletwo .twotop{
		margin-bottom: 0.6rem;
	}
	.moduletwo .twotop view:first-child{
		font-size: 1rem;
	}
	.moduletwo .module{
		padding: 5% 0;
	}
	.moduletwo .module .text text{
		margin: 2% 0;
	}
</style>
