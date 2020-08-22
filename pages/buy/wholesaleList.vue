<template>
	<view class="box">
		<view class="top FX-sa">
			<text v-for="(v,i) in arr">{{v.title}}</text>
		</view>
		<!-- <view class="" v-if="arrbool"> -->
			<view class="divcs">
				<view class="div FX-sa" v-for="(v,i) in arrall">
					<text class="w30 FX-c">{{v.title}}</text>
					<text>{{v.price}}</text>
					<text>{{v.prices}}</text>
					<text>{{v.make}}</text>
					<text>{{v.float}}</text>
				</view>
			</view>
		<!-- </view> -->
		<!-- <view class="F-xy" v-else>
			<image></image>
			<text>暂无数据</text>
		</view> -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				arr:[
					{id:'1',title:'商品名称'},
					{id:'1',title:'剩余量'},
					{id:'1',title:'买/卖价格'},
					{id:'1',title:'买/卖'},
					{id:'1',title:'操作'},
				],
				arrbool:false,
				arrall:[
					{title:'艾度至亚麻籽油66002',price:'108',prices:'129',make:'4562',float:'0.01%'},
					{title:'艾度至亚麻籽油66002',price:'108',prices:'129',make:'4562',float:'0.01%'},
				]
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
	.top{
		padding: 4% 0;
		background-color: rgb(238,238,238);
	}
	.top text:first-child{
		width: 30%;
		text-align: center;
	}
	
	.divcs .div{
		padding: 4% 0; 
	}
	.divcs .div:nth-child(odd){
		background-color: #FFFFFF;
	}
	.divcs .div:nth-child(even){
		background-color: rgb(242,249,255);
	}
	
</style>
