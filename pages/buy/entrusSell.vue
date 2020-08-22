<template>
	<view class="box">
		<!-- <view class="top FX-sa">
			<text data-id='1' :class="[cid=='1'?'active w50 t-center':'w50 t-center']" @tap="selectState">
				摘牌卖出
			</text>
			<text data-id='2' :class="[cid=='2'?'active w50 t-center':'w50 t-center']" @tap="selectState">
				挂牌卖出
			</text>
		</view>
		<view class="divcs" v-if="arrbool">
			<view class="div" v-if="cid==1">
				<view class="FX-sb FY-c">
					<text>商品名称</text>
					<text>云之酵1</text>
				</view>
				<view class="FX-sb FY-c">
					<text>商品代码</text>
					<text>云之酵1</text>
				</view>
				<view class="FX-sb FY-c">
					<text>指导价范围</text>
					<text>{{324}}</text>
				</view>
				<view class="FX-sb FY-c">
					<text>卖出价格</text>
					<input class="jiage" type="number" :value="val" />
				</view>
				<view class="FX-sb FY-c">
					<text>可卖出数量</text>
					<text>{{0}}</text>
				</view>
				<view class="FX-sb FY-c">
					<text>卖出数量</text>
					<view class="FY-c FX-sb w50">
						<view class="valnum FX">
							<button type="primary" @click="valnume">-</button>
							<input class="t-center" type="text" :value="valnum" @input="inputChange"/>
							<button type="primary" @click="valnuma">+</button>
						</view>
						<button class="but1 F-xy">全部</button>
					</view>
				</view>
				<view class="butcs">
					<button class="" type="primary">提交</button>
				</view>
			</view>
			<view class="div" v-if='cid==2'>
				<view class="FX-sb FY-c">
					<text>商品名称</text>
					<text>云之酵2</text>
				</view>
				<view class="FX-sb FY-c">
					<text>商品代码</text>
					<text>云之酵2</text>
				</view>
				<view class="FX-sb FY-c">
					<text>指导价范围</text>
					<text>{{324}}</text>
				</view>
				<view class="FX-sb FY-c">
					<text>卖出价格</text>
					<input class="jiage" type="number" :value="vals" />
				</view>
				<view class="FX-sb FY-c">
					<text>可卖出数量</text>
					<text>{{0}}</text>
				</view>
				<view class="FX-sb FY-c">
					<text>卖出数量</text>
					<view class="FY-c FX-sb w50">
						<view class="valnum FX">
							<button type="primary" @click="valnumes">-</button>
							<input class="t-center" type="text" :value="valnums" @input="inputChanges"/>
							<button type="primary" @click="valnumas">+</button>
						</view>
						<button class="but1 F-xy">全部</button>
					</view>
				</view>
				<view class="butcs">
					<button class="" type="primary">提交</button>
				</view>
			</view>
		</view> -->
		
		<view class="top FX-sa">
			<!-- <text data-id='2' class="active w50 t-center">
				挂牌卖出
			</text> -->
		</view>
		<view class="div">
			<view class="FX-sb FY-c">
				<text>商品名称</text>
				<text>{{module.g_title}}</text>
			</view>
			<view class="FX-sb FY-c">
				<text>商品代码</text>
				<text>{{module.g_code}}</text>
			</view>
			<view class="FX-sb FY-c">
				<text>指导价范围</text>
				<text>{{module.ut_minprice}}~{{module.ut_maxprice}}</text>
			</view>
			<view class="FX-sb FY-c">
				<text>卖出价格</text>
				<input class="jiage t-right" type="number" :value="module.ut_price"/>
			</view>
			<view class="FX-sb FY-c">
				<text>可卖出数量</text>
				<text>{{module.g_inv}}</text>
			</view>
			<view class="FX-sb FY-c">
				<text>卖出数量</text>
				<view class="FY-c FX-sb w50">
					<view class="valnum FX">
						<button type="primary" @click="valnumes">-</button>
						<input class="t-center" type="text" :value="cnum" @input="inputChanges"/>
						<button type="primary" @click="valnumas">+</button>
					</view>
					<button class="but1 F-xy" @click="allnum(module.g_inv)">全部</button>
				</view>
			</view>
			<view class="butcs">
				<button class="" type="primary">提交</button>
			</view>
		</view>
		
	</view>
</template>

<script>
	import App from '../../App.vue'
	
	export default {
		data() {
			return {
				module:'',
				ginv:'',
				cnum:'',
				
				val:'325',
				vals:'325',
				number:'1',
				numbers:'2',
				valnum:'0',
				valnums:'0',
				arrbool:false,
				cid:''
			}
		},
		onLoad(e) {
			var that = this;
			that.cid=e.id;
			that.cnum=e.num;
			uni.getStorage({
			    key: 'token',
			    success: function (res) {
			        // console.log(res);
					uni.request({
					    url: App.checkEntrusCanSell,
						method: 'POST',
					    header: {'Authorization':'27AB7E898911F5BBCAE2059BC2BF5A5E'},
						data:{'g_id':that.cid},
					    success: (res) => {
					        console.log(res.data);
							that.module=res.data.data;
							that.ginv=res.data.data.g_inv;
							that.arrbool=true;
					    }
					});
			    }
			});
			
		},
		methods: {
			allnum(e){
				var that =this;
				console.log(e);
				that.cnum=e;
			},
			selectState(e){
				var that = this;
				console.log(e)
				that.cid=e.currentTarget.dataset.id
				console.log(e.currentTarget.dataset.id)
			},
			inputChange(e){
				var that = this;
				that.valnum = e.detail.value
				console.log(e.detail.value)
			},
			inputChanges(e){
				var that = this;
				that.valnums = e.detail.value
				console.log(e.detail.value)
			},
			valnume(){
				var that = this;
				that.valnum--
			},
			valnuma(){
				var that = this;
				that.valnum++
			},
			valnumes(){
				var that = this;
				that.valnums--;
				if(that.cnum<=1){
					that.cnum=1;
				}else{
					that.cnum--;
				}
				// if(that.cnum>1){
				// 	that.cnum-=10;
				// }else{
				// 	that.cnum=0;
				// }
			},
			valnumas(){
				var that = this;
				that.valnums++;
				if(that.cnum>=that.ginv){
					that.cnum=that.ginv;
				}else{
					that.cnum++;
				}
				// if(that.cnum<that.module.g_inv){
				// 	that.cnum+=10;
				// }
			}
		}
	}
</script>

<style>
	.box{
		background-color: rgb(245,245,245);
		min-height: calc(100vh);
	}
	.top text{
		padding:5%;
		background-color: #fff;
	}
	.top .txt{
		/* color: #000000; */
		text-decoration:none;
		font-size: 0.8rem;
	}
	.active{
		color: orangered;
		border-bottom: 1px solid orangered;
	}
	.divcs{
		overflow: hidden;
		height: calc(60vh);
	}
	.div{
		height: inherit;
		/* padding: 2%; */
	}
	.div>view{
		min-height: 1rem;
		/* margin: 2%; */
		padding: 4%;
		border-top: 1px solid #ccc;
		background-color: #fff;
	}
	.div>view:first-child{
		margin: 0;
		padding: 2% 4%;
	}
	.div>view:last-child{
		padding: 2%;
		margin: 4%;
		background-color: rgb(245,245,245);
	}
	.div .jiage{
		padding: 0;
		margin: 0;
		border: 1px solid #ccc;
	}
	.div button{
		height: 1.5rem;line-height: 1.5rem;border:1px solid transparent;
		color: orange;background-color: transparent;outline: none;
		margin: 0;padding: 0;
	}
	.div button:after{content: "";display: block;clear: both;border:1px solid transparent;}
	.div .valnum{
		border:1px solid #999;
	}
	.div .valnum button{
		width: 1.2rem;height: 1.2rem;
		color: #000;line-height: 1rem;
		border-radius: 0;
		background-color: rgb(248,248,248);  
	}
	.div .valnum input{
		width: 2rem;
	}
	.div .but1{
		color: #fff;
		background-color: orangered;
		padding: 5%;
	}
	.div .butcs{
		border: none;
	}
	.div .butcs button{
		height: 2rem;
		line-height: 2rem;
		color: #fff;
		background-color: orangered;
	}
</style>
