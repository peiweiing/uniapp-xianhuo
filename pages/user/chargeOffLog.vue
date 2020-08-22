<template>
	<view class="box">
		<view class="module" v-for='(v,i) in arr'>
			<view class="top FX-sb">
				<text>-{{v.price}}元</text>
				<text>{{v.state}}</text>
			</view>
			<view class="end FX-sb">
				<text>{{v.code}}</text>
				<text>{{v.date}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				arr:[
					{price:'2000',state:'成功',code:'1234512354',date:'2020-00-08'},
					{price:'2000',state:'成功',code:'1234512354',date:'2020-00-08'},
					{price:'2000',state:'成功',code:'1234512354',date:'2020-00-08'},
					{price:'2000',state:'成功',code:'1234512354',date:'2020-00-08'},
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
	.module{
		padding: 3%;
		border-bottom: 1px solid rgb(240,240,240);
	}
	.module .top{
		margin-bottom: 2%;
	}
	.module .top text:first-child{
		color: orangered;
		font-size: 0.8rem;
	}
	.module .end{
		color: rgb(200,200,200);
	}
</style>
