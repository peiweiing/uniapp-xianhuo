
<script>
	// 账号登录
	const login = "http://api.lovehou.com/api/login";
	//验证码登录
	// const login = "http://api.lovehou.com/api/login";
	//修改密码
	// const updatepwd = "http://api.lovehou.com/api/updatepwd";
	//我的挂单列表
	const getEntrusList = "http://api.lovehou.com/api/goods/getEntrusList";
	//商品列表
	const list = "http://api.lovehou.com/api/goods/list";
	//商品详情
	const detail = "http://api.lovehou.com/api/goods/detail";
	//新品列表
	const newgoods = "http://api.lovehou.com/api/goods/newgoods";
	//挂牌买入列表
	const getEntrusBuyList = "http://api.lovehou.com/api/goods/getEntrusBuyList";
	//挂牌卖出列表
	const getEntrusSellList = "http://api.lovehou.com/api/goods/getEntrusSellList";
	//挂牌买入页面
	const entrusBuyList = "http://api.lovehou.com/api/goods/entrusBuyList";
	//挂牌卖出页面
	const checkEntrusCanSell = "http://api.lovehou.com/api/goods/checkEntrusCanSell";
	export default {
		login,
		// updatepwd,
		getEntrusList,
		list,
		detail,
		newgoods,
		getEntrusBuyList,
		getEntrusSellList,
		entrusBuyList,
		checkEntrusCanSell,
		
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	/* html{font-size:26.67vw;} */
	body,ol,ul,h1,h2,h3,h4,h5,h6,p,th,td,dl,dd,form,fieldset,legend,input,textarea,select{margin:0;padding:0;}
	body{font-size:0.1rem;background:#fff;}
	a{color:#172c45;text-decoration:none;}
	a:hover{color:#cd0200;text-decoration:underline;}
	ul,ol,li{list-style:none;}
	img{border:0;vertical-align:middle;}
	table{border-collapse:collapse;border-spacing:0;}
	.min-height{min-height:calc(100vh)}.min-width{min-width: calc(100vw);}
	

	/* 定位 */
	.pon{position:static!important;}
	.por{position:relative!important;}
	.poa{position:absolute!important;}
	.pof{position:fixed!important;}
	.pos{position:sticky!important;}
	/* 浮动 */
	.float-l{float:left!important;}
	.float-r{float:right!important;}
	/* 清除浮动*/
	.clear:after{content:"";display:block;clear:both}
	/* 隐藏 */
	.none{display:none;}
	.hidden{visibility:hidden;}
	.opacity{opacity:0;}
	.flow-auto{overflow:auto;}
	.flow-hidden{overflow:hidden;}
	.flow-x{overflow-x:hidden;}
	.flow-y{overflow-y:hidden;}
	.noborder{border:none;}
	/* 层级 */
	.z9{z-index: 9;}
	.z99{z-index: 99;}
	.z999{z-index: 999;}
	.z9999{z-index: 9999;}
	
	/* 主色调 */
	.bgcColor{background-color: orangered;}
	.bgcImg{background-image: url() no-repeat;}
	
	/* 字体样式 */
	.f06rem{font-size: 0.6rem;}
	.f07rem{font-size: 0.7rem;}
	.f08rem{font-size: 0.8rem;}
	.f09rem{font-size: 0.9rem;}
	.f1rem{font-size: 1rem;}
	/* 字体加粗 */
	.f-bold{font-weight:bold;}
	/* 字体不换行 */
	.f-nowrap{white-space:nowrap;}
	/* 首行缩进 */
	.f-indent{text-indent:2em;}
	/* 字符间距 */
	.f-spacing{letter-spacing:1em;}
	/* 单词及字母换行 */
	.f-all{word-wrap:break-word;word-break:break-all;}
	/* 将长串字母或长单词自动换行 */
	.f-wrap{word-wrap:break-word;}
	/* 将完整的单词拆分自动换行 */
	.f-break{word-break:break-all;}
	/* 文本溢出隐藏 */
	.f-hidden3{
	    overflow:hidden;/*溢出隐藏*/
	    text-overflow: ellipsis;/*超出部分显示省略号*/
	    display:-webkit-box;/*弹性盒*/
	    -webkit-box-orient:vertical;/*设置对象内元素的排列方式为垂直*/
	    -webkit-line-clamp:3;/*限制块元素文本行数*/
	}
	.f-hidden{
	    overflow:hidden;/*溢出隐藏*/
	    white-space:nowrap; /*不换行*/
	    text-overflow:ellipsis;/*超出部分显示省略号*/
	    -o-text-overflow:ellipsis;
	}
	
	.t-left{text-align:left;}
	.t-center{text-align:center;}
	.t-right{text-align:right;}
	
	.v-top{vertical-align:top;}
	.v-middle{vertical-align:middle;}
	.v-bottom{vertical-align:bottom;}
	
	.w10{width:10%;}.w20{width:20%;}.w30{width:30%;}.w40{width:40%;}.w50{width:50%;}
	.w60{width:60%;}.w70{width:70%;}.w80{width:80%;}.w90{width:90%;}.w100{width:100%;}
	.w2{width:50%;}.w3{width:33.333%;}.w4{width:25%;}.w5{width:20%;}
	.w6{width:16.666%;}.w7{width:14.285%;}.w8{width:12.5%;}.w9{width:11.111%;}
	
	.f1{flex:1;}.f2{flex:2;}.f3{flex:3;}.f4{flex:4;}.f5{flex:5;}
	.f6{flex:6;}.f7{flex:7;}.f8{flex:8;}.f9{flex:9;}
	.f10{flex:0 0 10%}.f16{flex:0 0 16.666%;}.f20{flex:0 0 20%;}.f25{flex:0 0 25%;}
	.f33{flex:0 0 33.333%;}.f50{flex:0 0 50%;}.f100{flex:0 0 100%;}
	
	.o1{order:1}.o2{order:2}.o3{order:3}.o4{order:4}.o5{order:5}

	.block{display:block!important;}/*块级元素*/
	.blocks{display:inline-block!important;}/*内联元素*/
	.boxing{box-sizing:border-box!important;}
	.flex{display: box;display: -webkit-box;
	    display: -moz-box;display: -ms-flexbox;
	    display: -webkit-flex;display:flex!important;
	}/*块级弹性盒*/
	.flexs{display: box;display: -webkit-box;
	    display: -moz-box;display: -ms-flexbox;
	    display: -webkit-flex;display:inline-flex!important;
	}/*内联弹性盒*/
	
	.F-xy{display:flex!important;justify-content:center!important;align-items:center!important;}

	.F-wrap{display:flex!important;flex-wrap:wrap!important;}

	.F-wrapr{display:flex!important;flex-wrap:wrap-reverse!important;}
	
	.FX{display:flex!important;flex-direction:row!important;}

	.FX-r{display:flex!important;flex-direction:row-reverse!important;}
	
	.FY{display:flex!important;flex-direction:column!important;}

	.FY-r{display:flex!important;flex-direction:column-reverse!important;}
	
	.FX-c{display:flex!important;justify-content:center!important;}
	.FX-sb{display:flex!important;justify-content:space-between!important;}
	.FX-sa{display:flex!important;justify-content:space-around!important;}
	.FX-fs{display:flex!important;justify-content:flex-start!important;}
	.FX-fe{display:flex!important;justify-content:flex-end!important;}

	.FY-c{display:flex!important;align-items:center!important;}
	.FY-b{display:flex!important;align-items:baseline!important;}/*以首行基线对齐*/
	.FY-fe{display:flex!important;align-items:flex-end!important;}
	.FY-fs{display:flex!important;align-items:flex-start!important;}

</style>
