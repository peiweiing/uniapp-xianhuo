<template>
	<view class="box">
		<view class="search FY-c">
			<image class="img" src="../../static/search.png" mode=""></image>
			<input type="text" placeholder="商品名/商品编码" />
		</view>
		<view class="divtop FX-sa">
			<text class="w20" v-for="(v,i) in arr">{{v.title}}</text>
		</view>
		<view v-if="arrbool">
			<view class="div FX-sa FY-c" v-for="(v,i) in module" v-if="arrbool">
				<text class="w30 FX-c">{{v.g_title}}</text>
				<text class="w20">{{v.ut_num}}</text>
				<text class="w20">{{v.ut_price}}</text>
				<button class="w20" @click="fun(v.g_id)">买入</button>
			</view>
		</view>
		
		<view class="F-xy FY" v-else>
			<image></image>
			<text>暂无数据</text>
		</view>
		
		<view class="zhezhaocs F-xy" v-if="arrbut">
			<view class="zhezhao w80">
				<view class="top t-center">提示</view>
				<view class="cent">
					<view class="FX-sb">
						<text>剩余挂牌量</text>
						<text>{{butmake}}</text>
					</view>
					<view class="FX-sb">
						<text>买入数量</text>
						<view class="valnum FX">
							<button class='F-xy' type="primary" @click="valnumes">-</button>
							<input class="t-center" type="text" :value="valnums" @input="inputChanges"/>
							<button class='F-xy' type="primary" @click="valnumas">+</button>
						</view>
					</view>
				</view>
				<view class="end FX-sb">
					<button class="butt1 w50" type="primary" @click="close">取消</button>
					<button class="butt2 w50" type="primary" @click="confirm">确定</button>
				</view>
			</view>
		</view>
			
	</view>
</template>

<script>
	import App from '../../App.vue'
	export default {
		data() {
			return {
				arr:[
					{id:'1',title:'商品名称'},
					{id:'2',title:'剩余量'},
					{id:'3',title:'买入价格'},
					{id:'4',title:'操作'},
				],
				arrall:[
					{id:'1',title:'艾度至亚麻籽油66002',price:'101',prices:'121',make:'4562',float:'0.01%'},
					{id:'2',title:'艾度至亚麻籽油66002',price:'102',prices:'122',make:'4562',float:'0.01%'},
					{id:'3',title:'艾度至亚麻籽油66002',price:'103',prices:'123',make:'4562',float:'0.01%'},
					{id:'4',title:'艾度至亚麻籽油66002',price:'104',prices:'124',make:'4562',float:'0.01%'},
				],
				arrbool:false,
				arrbut:false,
				valnums:'1',
				butmake:'',
				tid:''
			}
		},
		onLoad() {
			var that =this;
			uni.getStorage({
			    key: 'token',
			    success: function (res) {
			        // console.log(res);
					uni.request({
					    url: App.getEntrusBuyList,
						method: 'POST',
					    header: {'Authorization':'27AB7E898911F5BBCAE2059BC2BF5A5E'},
					    success: (res) => {
					        console.log(res.data);
							that.module=res.data.data;
							that.butmake=res.data.data[0].ut_num;
							that.arrbool=true;
					    }
					});
			    }
			});
			
		},
		methods: {
			fun(e){
				console.log(e)
				var that = this;
                // var id = e; 
				that.tid = e;
				that.arrbut=true;
				// valnums = that.valnums;
				// butmake = that.butmake;
				// console.log(this.butmake)
			},
			inputChanges(e){
				var that = this;
				that.valnums = e.detail.value
				console.log(e.detail.value)
			},
			valnumes(){
				var that = this;
				if(that.valnums>1){
					that.valnums--;
				}else{
					that.valnums=1
				}
			},
			valnumas(){
				var that = this;
				if(that.valnums<that.butmake){
					that.valnums++;
				}else{
					that.valnums=that.butmake
				}
			},
			close(e){
				var that =this;
				that.arrbut=false;
			},
			confirm(e){
				var that = this;
				var id = that.tid;
				var num = that.valnums;
				uni.navigateTo({
					url: 'entrusBuy?id='+id+'&num='+num,
				});
				console.log(id)
			}
		}
	}
</script>

<style>
	.box{
		min-height: calc(100vh);
		/* background-color: rgb(245,245,245); */
		background-color: rgb(238,238,238);
		padding-top: 3%;
	}
	.search{
		background-color: #fff;
		border-radius: 40rpx;
		padding: 2%;
		margin: 0 2%;
	}
	.search .img{
		height: 1rem;width: 1rem;
	}
	.divtop{
		padding: 4% 0;font-size: 1rem;
		background-color: rgb(238,238,238);
		text-align: center;
	}
	.divtop text:first-child{
		width: 30%;
	}
	.div{padding: 4% 0;text-align: center;font-size: 0.8rem;}
	.div button{
		height: 1.5rem;line-height: 1.5rem;border:1px solid transparent;
		color: orange;background-color: transparent;outline: none;
		margin: 0;padding: 0;
	}
	.div button:after{content: "";display: block;clear: both;border:1px solid transparent;}
	.div:nth-child(odd){
		background-color: #FFFFFF;
	}
	.div:nth-child(even){
		background-color: rgb(242,249,255);
	}
	
	.zhezhaocs{
		width: 100%;height: 100%;
		position: fixed;top: 0;
		background-color: rgba(100,100,100,0.6);
	}
	.zhezhaocs .zhezhao{
		background-color: #fff;
		border-radius: 20rpx;
	}
	.zhezhao .top{
		padding: 3%;
		border-bottom: 1px solid rgb(220,220,220);
	}
	.zhezhao .cent{
		padding: 2% 5%;
	}
	.zhezhao .cent>view{
		padding: 5%;
	}
	.zhezhao .end button{
		border-radius: 0px;
	}
	.zhezhao .end .butt1{
		color: #000000;
		background-color: rgb(230,230,230);
		border-radius: 0 0 0 20rpx;
	}
	.zhezhao .end .butt2{
		background: orangered;
		border-radius: 0 0 20rpx 0;
	}
	.zhezhao .valnum{
		border:1px solid #999;
	}
	.zhezhao .valnum button{
		width: 1.2rem;height: 1.2rem;
		color: #000;line-height: 1.2rem;
		border-radius: 0px;text-align: center;
		background-color: rgb(248,248,248);  
	}
	.zhezhao .valnum button:after{
		border-radius: 0px;border: none;
	}
	.zhezhao .valnum input{
		width: 2rem;
	}
</style>
