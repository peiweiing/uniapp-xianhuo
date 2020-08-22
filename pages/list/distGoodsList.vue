<template>
	<view class="box">
		
		<swiper class="swiper" :autoplay="autoplay" :circular="circular" :interval="interval" :duration="duration" :indicator-dots="indicator">
			<swiper-item v-for="(v,i) in swiper">
				<view class="swiper-item">
					<!-- <navigator :url="v.url" style="height: inherit;"> -->
						<image class="img" :src="v.img" mode=""></image>
					<!-- </navigator> -->
				</view>
			</swiper-item>
		</swiper>
		
		<view class="news">
			<view class="FX-sb newtop">
				<view class="FY-c">
					<image class="icon" src="../../static/gonggao.png" mode=""></image>
					<text>公告</text>					
				</view>
				<view>
					<!-- <text>更多</text>
					<text>></text> -->
				</view>
			</view>
			<view class="newend">
				<swiper class="swipers" :current="tabIndex" :autoplay="autoplay" :circular="circular" :interval="interval" :duration="duration" :vertical="vertical" @change="tabChange">
					<swiper-item v-for="(v,i) in news">
						<view class="swiper-item FY FX-sa">
							<navigator class="FY-c" :url="v.url1" style="height: inherit;">
								<view class="FX-sb w100">
									<view class="FX FY-c">
										<view class="rdian"></view>
										<text>{{v.text}}</text>
									</view>
									<text>{{v.time}}</text>
								</view>
							</navigator>
							<navigator class="FY-c" :url="v.url2" style="height: inherit;">
								<view class="FX-sb w100">
									<view class="FX FY-c">
										<view class="rdian"></view>
										<text>{{v.texts}}</text>
									</view>
									<text>{{v.times}}</text>
								</view>
							</navigator>
						</view>
					</swiper-item>
				</swiper>
			</view>
		</view>
		
		<view class="module one">
			<view class="FX-sb FY-c onetop">
				<view class="FY-c">
					<image class="icon" src="../../static/news.png"></image>
					<text>新品推荐</text>					
				</view>
				<view>
					<!-- <text>更多</text>
					<text>></text> -->
				</view>
			</view>
			<view class="oneend FX"> 
				<navigator class="" v-for="(v,i) in modulea" :url="'distGoodsDetail?id='+v.g_id">
					<view class="">
						<image class="img" :src="'https://xianhuo.vippays.cn'+v.g_pic" mode=""></image>
					</view>
				</navigator>
			</view>
		</view>
		
		<view class="module two" v-for="(v,i) in moduleb">
			<view class="FX-sb twotop">
				<view class="FX">
					<view class="rig"></view>
					<view>
						商品编码
						<text class="blod">{{v.g_code}}</text>
					</view>
				</view>
				<view>
					<!-- <text>></text> -->
				</view>
			</view>
			<view class="FX-sb F-wrap"> 
				<navigator class="w100" :url="'distGoodsDetail?id='+v.g_id">
					<view class="FX-sb twoend">
						<image class="img w30" :src="'https://xianhuo.vippays.cn'+v.g_pic" mode=""></image>
						<view class="text w70 FY FX-sa">
							<text class="blod">{{v.g_title}}</text>
							<view class="F-wrap FX-sb w100">
								<view class="w2">拼团价：<text class="texts">{{v.g_price}}</text>元</view>
								<view class="w2">批发价：<text class="texts">{{v.g_pfprice}}</text>元</view>
								<view class="w2">成交量：<text class="blod">{{v.g_salevol}}</text></view>
							</view>
							<view class="FX-sa">
								<button class="w30">买入</button>
								<button class="w30">卖出</button>
							</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		
	</view>
</template>

<script>
	import App from '../../App.vue'
	export default {
		data() {
			return {
	            autoplay: true,
				circular: true,
				vertical: true,
				indicator:true,
	            interval: 4000,
	            duration: 1000,
				tabIndex:0,
				
				swiper:[
					{img:'../../static/banner@3x.png',url:'detail'},
					{img:'../../static/banner@3x.png',url:'detail'},
					{img:'../../static/banner@3x.png',url:'detail'},
				],
				news:[
					{text:'今日公告，今日首播',time:'4-26',url1:'',texts:'今日公告，今日新闻，今日首播',times:'4-26',url2:'',},
					{text:'今日公告，今日首播',time:'4-26',url1:'',texts:'今日公告，今日新闻，今日首播',times:'4-26',url2:'',},
					{text:'今日公告，今日首播',time:'4-26',url1:'',texts:'今日公告，今日新闻，今日首播',times:'4-26',url2:'',},
				],
				moduleone:[
					{img:'../../static/img_dianpu@3x.png',url:'detail'},
					{img:'../../static/img_dianpu@3x.png',url:'detail'},
					{img:'../../static/img_dianpu@3x.png',url:'detail'},
					{img:'../../static/img_dianpu@3x.png',url:'detail'},
					{img:'../../static/img_dianpu@3x.png',url:'detail'},
				],
				moduletwo:[
					{id:'1',img:'../../static/img_dianpu@3x.png',title:'云之酵1（加强版）',code:'645623',pingtuan:'325.0',pifa:'50.0',chengjiao:'64945',url:'detail'},
					{id:'2',img:'../../static/img_dianpu@3x.png',title:'云之酵2（加强版）',code:'645623',pingtuan:'325.0',pifa:'50.0',chengjiao:'64945',url:'detail'},
				],
				modulea:[],
				moduleb:[],
				eid:''
			}
		},
		onLoad() {
			var that =this;
			console.log('onload:')
			uni.getStorage({
			    key: 'token',
			    success: function (res) {
			        // console.log(res);
					uni.request({
					    url: App.newgoods,
						method: 'POST',
					    // header: {'Authorization':res.data},
					    header: {'Authorization':'27AB7E898911F5BBCAE2059BC2BF5A5E'},
					    success: (res) => {
					        console.log(res.data);
							that.modulea=res.data.data;
					    }
					});
			    }
			});
			uni.getStorage({
			    key: 'token',
			    success: function (res) {
			        // console.log(res);
					uni.request({
					    url: App.list,
						method: 'POST',
					    header: {'Authorization':'27AB7E898911F5BBCAE2059BC2BF5A5E'},
					    success: (res) => {
					        console.log(res.data);
							that.moduleb=res.data.data;
					    }
					});
			    }
			});
			
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
	.swiper{
		/* height: 4rem; */
	}
	.swiper .swiper-item{
		height: inherit;
	}
	.swiper .swiper-item .img{
		width: 100%;
		height: 100%;
	}
	.swipers{
		height: 2rem;
	}
	.swipers .swiper-item{
		height: inherit;
	}
	.swipers .uni-swiper-slides{
		/* background-color: #EAD6EE; */
		background-color: rgb(245,245,245);
	}
	.blod{
		color: #000;
		font-weight: bolder;
	}
	.module{
		padding: 2%;
		background-color: #fff;
	}
	.module .rig{
		width: 12rpx;
		margin-right: 10rpx;
		border-top: 36rpx solid orangered;
	}
	.news{
		padding: 2%;
		background-color: #fff;
	}
	.news .icon{
		width: 1rem;height: 1rem;
	}
	.news .swipers{
		padding: 2%;
		background-color: rgb(245,245,245);
	}
	.news .newtop{
		margin-bottom: 2%;
	}
	.news .rdian{
		width: 16rpx;
		height: 16rpx;
		margin-right: 10rpx;
		border-radius: 50%;
		background-color: orangered;
	}
	.one{
		margin-bottom: 2%;
	}
	.one .icon{
		width: 1rem;height: 1rem;
	}
	.one .onetop{
		margin-bottom: 2%;
	}
	.one .oneend{
		overflow-y: auto;
	}
	.one .oneend .img{
		width: 5.4rem;
		height: 5.4rem;
		margin-right: 0.4rem;
	}
	.two .img{
		width: 4.4rem;
		height: 4.6rem;
	}
	.two .twotop{
		margin-bottom: 2%;
	}
	.two .twoend .text{
		color: #999999;
	}
	.two .twoend .text text{
		font-size: 0.8rem;
	}
	.two .twoend .texts{
		color: orangered;
	}
	.two .twoend button{
		height: 1.3rem;
		line-height: 1.3rem;
		border-radius: 40rpx;
		font-size: 0.6rem;
		color: #fff;
	}
	.two .twoend button:first-child{
		background: linear-gradient(to right, rgb(255,131,86) , rgb(255,80,17));
	}
	.two .twoend button:last-child{
		background: linear-gradient(to right, rgb(255,114,164) , rgb(252,84,120));
	}
</style>
