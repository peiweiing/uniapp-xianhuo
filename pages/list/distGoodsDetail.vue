<template>
	<view>
		<swiper class="swiper" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
			<swiper-item v-for="(v,i) in module">
				<view class="swiper-item">
					<image class="img" :src="'https://xianhuo.vippays.cn'+module.g_pic" mode=""></image>
				</view>
			</swiper-item>
		</swiper>
		
		<view class="module two">
			<view class="twotop FX">
				<view class="rig"></view>
				<view>
					商品编码
					<text class="blod">{{module.g_code}}</text>
				</view>
			</view>
			<view class="twoend FX-sb F-wrap">
				<text class="blod">{{module.g_title}}</text>
				<view class="F-wrap FX-sb w100 text">
					<view class="w2">拼团价：<text class="texts">{{module.g_price}}</text>元</view>
					<view class="w2">批发价：<text class="texts">{{module.g_pfprice}}</text>元</view>
					<view class="w2">成交量：<text class="blod">{{module.g_salevol}}</text></view>
				</view>
				
			</view>
			<view class="three">
				<image class="img" :src="'https://xianhuo.vippays.cn'+module.g_pic" mode=""></image>
			</view>
		</view>
		
		
		<view class="module four FX-sa pof w100">
			<button class="w40">买入</button>
			<button class="w40">卖出</button>
		</view>
	</view>
</template>

<script>
	import App from '../../App.vue'
	export default {
		data() {
			return {
				detailID:'',
				swiper:[
					{img:'../../static/banner@3x.png',},
					{img:'../../static/banner@3x.png',}
				],
				moduletwo:[
					{img:'../../static/banner@3x.png',title:'云之酵（加强版）',code:'645623',pingtuan:'325.0',pifa:'50.0',chengjiao:'64945',url:'detail'},
				],
				image:[
					{img:'../../static/banner@3x.png',},
					{img:'../../static/banner@3x.png',},
					{img:'../../static/banner@3x.png',}
				],
				module:[]
			}
		},
		onLoad(e) {
			var eid =e.id
			var that =this;
			that.detailID = eid;
			var gid ={
				'g_id':that.detailID
			}
			var tok ={
				'Authorization':'27AB7E898911F5BBCAE2059BC2BF5A5E'
			}
			console.log(eid)
			uni.getStorage({
			    key: 'token',
			    success: function (res) {
			        // console.log(res);
					uni.request({
					    url: App.detail,
						method: 'POST',
					    header: tok,
						data:gid,
					    success: (res) => {
					        console.log(res);
							that.module=res.data.data;
					        console.log(that.module.g_code);
					    }
					});
			    }
			});
			
		},
		methods: {
			// newarr(){
			// 	var demoarr=this.module.filter((v,i)=>{
			// 		if(v.id==this.detailID){
			// 			return v;
			// 			console.log(v)
			// 		}
			// 	})
			// 	return demoarr
			// 	console.log(demoarr)
			// }
		}
	}
</script>

<style>
	.module{
		padding: 2%;
		background-color: #fff;
	}
	.module .rig{
		width: 12rpx;
		margin-right: 10rpx;
		border-top: 36rpx solid orangered;
	}
	.swiper .swiper-item{
		height: inherit;
	}
	.swiper .img{
		width: 100%;
		height: inherit;
	}
	.two .img{
		width: 4.4rem;
		height: 4.6rem;
	}
	.two .twotop{
		margin-bottom: 2%;
	}
	.two .twoend>text{
		font-size: 0.8rem;
	}
	.two .twoend .text{
		color: #999999;
	}
	.two .twoend .texts{
		color: orangered;
	}
	.three .img{
		width: 100%;
		height: 16rem;
	}
	.four{
		background-color: #fff;
		bottom: 0;
	}
	.four button{
		height: 1.6rem;
		line-height: 1.6rem;
		border-radius: 10rpx;
		font-size: 0.6rem;
		padding: 0 10%;
		color: #fff;
	}
	.four button:first-child{
		background: linear-gradient(to bottom, #f78ca0 , #fe9a8b);
	}
	.four button:last-child{
		background: linear-gradient(to bottom, #b12a5b , #ff8177);
	}
</style>
