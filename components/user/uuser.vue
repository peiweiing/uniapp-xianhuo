<template>
	<view class="div FX-sb">
		<view class="divl FX-fs w40">
			<image class="img" :src="imgsrc" mode=""></image>
			<text>{{text}}</text>
		</view>
		<view class="divr FX-fe w20">
			<slot></slot>
			<text>></text>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			imgsrc: String,
			text: String,
			
		},
		data() {
			return {
				
			};
		},
	}
</script>

<style>
	.div{
		padding: 4% 2%;
	}
	.div .img{
		width: 1rem;
		height: 1rem;
		margin-right: 8%;
	}
</style>
