<template>
	<view>
		<view class="div FX-sa">
			<text class="w30 FX-c">{{title}}</text>
			<text class="w20">{{one}}</text>
			<text class="w20">{{two}}</text>
			<!-- <text>{{three}}</text>
			<slot>{{four}}</slot> -->
			<button class="w20">{{val}}</button>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			title:String,
			one:String,
			two:String,
			three:String,
			four:String,
			type:String,
			val:String
		},
		data() {
			return {
				
			};
		}
	}
</script>

<style>

	.div{
		padding: 4% 0; 
		text-align: center;
	}
	
	.div button{
		height: 1.5rem;line-height: 1.5rem;border:1px solid transparent;
		color: orange;background-color: transparent;outline: none;
		margin: 0;padding: 0;
	}
	.div button:after{content: "";display: block;clear: both;border:1px solid transparent;}
</style>
