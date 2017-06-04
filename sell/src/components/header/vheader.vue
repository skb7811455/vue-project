<template>
	<div class="vheader">
		<div class="content-wrapper">
			<div class="avatar">
				<img width="64" height="64" v-bind:src="seller.avatar"/>
			</div>
			<div class="content">
				<div class="title">
					<span class="brand"></span>
					<span class="name">{{seller.name}}</span>
				</div>
				<div class="description">
					{{seller.description}}/{{seller.deliveryTime}}分送达
				</div>
				<div v-if="seller.supports" class="support">
					<span class="icon" :class="classMap[seller.supports[0].type]"></span>
					<span class="text">{{seller.supports[0].description}}</span>
					<i class=""></i>
				</div>
			</div>
			<div v-if="seller.supports" class="support-count"  @click="showDetail">
				<span class="count">{{seller.supports.length}}个</span>
				<span class="icon-keyboard_arrow_right"></span>
			</div>
		</div>
		<div class="bulletin-wrapper"  @click="showDetail">
			<span class="bulletin-title"></span>
			<span class="bulletin-text">{{seller.bulletin}}</span>
			<i></i>
		</div>
		<div class="background">
			<img :src="seller.avatar" width="100%" height="100%"/>
		</div>
		<div class="detail" v-show="detailShow">
			<div class="detail-wrapper clearfix">
				<div class="detail-main">
					<h1 class="name">{{seller.name}}</h1>
					<div class="star-wrapper">
						<star :size="48" :score="seller.score"></star>
				    </div>
					<titleFlex text="优惠信息"></titleFlex>	
				    <ul v-if="seller.supports" class="supports">
				    	<li class="support-item" v-for="item in seller.supports">
				    		<span :class="classMap[item.type]" class="icon"></span>
				    		<span>{{item.description}}</span>
				    	</li>
				    </ul>
				    <titleFlex text="商家公告"></titleFlex>	 
				    <div class="bulletin">
				    	<p class="content">{{seller.bulletin}}</p>
				    </div>   
				</div>
			</div>
			<div class="detail-close">
				<span class="icon-close icon" @click="closeDetail"></span>
			</div>
		</div>
	</div>
</template>

<script>
	import star from '../star/star.vue';
	import titleFlex from '../titleFlex/titleFlex.vue';
	
	export default {
	  props: {
	  	seller:{
	  		type:Object
	  	}
	  },
	  created() {
	  	this.classMap=["decrease","discount","special","invoice","guarantee"];
	  },
	  data() {
	  	return {
	  		detailShow:false
	  	}
	  },
	  methods: {
	  	showDetail(){
	  		this.detailShow=true;
	  	},
	  	closeDetail(){
	  		this.detailShow=false;
	  	}
	  },
	  components: {
	  	"star":star,
	  	"titleFlex":titleFlex 
	  }
    }
</script>

<style>
 @import '/static/css/easydialog.min.css';
  	.clearfix{
    display: inline-block;
  	}
  	.clearfix:after{
    display: block;
    content: ".";
    height: 0;
    line-height: 0;
    clear:both;
    visibility: hidden;
  	}
	.vheader{
		color:#fff;
		position: relative;
		background: rgba(7,17,27,0.5);
		overflow: hidden;
	}
	.content-wrapper{
		padding: 24px 16px 38px 24px;
		font-size: 0;
		position: relative;
	}
	.content-wrapper .avatar{
		display: inline-block;
	}
	.content-wrapper .avatar img{
		border-radius: 2px;
	}
	.content-wrapper .content{
		display: inline-block;
		font-size: 14px;
		margin-left: 16px;
		vertical-align: top;
	}
	.content-wrapper .content .title{
		margin: 2px 0 8px 0;
	}
	.content-wrapper .content .title .brand{
		display:inline-block;
		width: 30px;
		height: 18px;
		vertical-align: top;
		background-size:30px 18px;
		background-image:url(brand@2x.png);
	}
	@media(-wekit-min-device-pixel-ratio:3){
		.content-wrapper .content .title .brand{
			background-image:url(brand@3x.png);
		}
	}
	.content-wrapper .content .title .name{
		margin-left: 6px;
		font-size: 16px;
		color: rgb(255,255,255);
		font-weight: bold;
		line-height: 18px;
	}
	.content-wrapper .content .title .description{
		font-size: 12px;
		color: rgb(255,255,255);
		font-weight: 200;
		line-height: 12px;
	}
	.content-wrapper .content .support{
		margin-top: 10px;
		font-size: 0;
	}
	.content-wrapper .content .support .icon{
		display: inline-block;
		width: 12px;
		height: 12px;
		margin-right: 4px;
		background-size: 12px 12px;
		background-repeat: no-repeat;
	}
	.content-wrapper .content .support .text{
		display: inline-block;
		line-height: 12px;
		color: rgb(255,255,255);
		font-weight: 200;
		font-size: 10px;
		vertical-align: top;
	}
	.content-wrapper .content .decrease{
		background-image:url(decrease_1@2x.png);
	}
	.content-wrapper .content .discount{
		background-image:url(discount_1@2x.png);
	}
	.content-wrapper .content .special{
		background-image:url(special_1@2x.png);
	}
	.content-wrapper .content .invoice{
		background-image:url(invoice_1@2x.png);
	}
	.content-wrapper .content .guarantee{
		background-image:url(guarantee_1@2x.png);
	}
	.content-wrapper .support-count{
		position: absolute;
		right: 12px;
		bottom: 18px;
		padding: 0 8px;
		height: 24px;
		line-height: 24px;
		background-color:rgba(0,0,0,0.2);
		text-align: center;
		border-radius: 14px;
	}
	.content-wrapper .support-count .count{
		color: #fff;
		display: inline-block;
		font-size: 10px;
	}
	.bulletin-wrapper{
		height: 28px;
		line-height: 28px;
		padding: 0 22px 0 12px;
		white-space: nowrap;
		overflow: hidden;	
		text-overflow:ellipsis;
		background-color: rgba(7,17,27,0.2);
	}
	.bulletin-wrapper .bulletin-title{
		display: inline-block;
		width: 22px;
		height: 12px;
		background-image: url(bulletin@2x.png);
		background-size: 22px 12px;
		background-repeat: no-repeat;
	}
	.bulletin-wrapper .bulletin-text{
		font-size: 10px;
		color: rgb(255,255,255);
		font-weight: 200;
		line-height: 28px;
		vertical-align: top;
	}
	.background{
		width: 100%;
		height: 100%;
		top:0;
		left: 0;
		position: absolute;
		z-index: -1;
		filter:blur(10px);
	}
	.detail{
		position: fixed;
		z-index:200;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		overflow: auto;
		background: rgba(7,17,27,0.8);
	}
	.detail .detail-wrapper{
		min-height: 100%;
		width: 100%;
	}
	.detail .detail-wrapper .detail-main{
		margin-top: 64px;
		padding-bottom: 64px;
		text-align: center;
		
	}
	.detail .detail-close{
		position:relative;
		width: 32px;
		height: 32px;
		font-size:20px;
		text-align: center;
		margin:-68px auto 0 auto;
		color: #fff;
	}
	.detail .name{
		font-size: 16px;
		font-weight: 700;
		color: rgb(255,255,255);
		line-height: 16px;
	}
	.star-wrapper{
		margin-top: 16px;
		height: 24px;
	}
	.detail .title{
		display: flex;
		width: 80%;
		margin: 28px auto 24px auto;
	}
	.detail .title .line{
		flex:1;
		border-bottom: 1px solid rgba(255,255,255,0.2);
		position: relative;
		top:-6px;
	}
	.detail .title .text{
		padding: 0 12px 0 12px;	
		font-size: 14px;
		font-weight: 700;
		color: rgb(255,255,255);
		line-height: 14px;
	}
	.detail .supports{
		width: 80%;
		margin: 0 auto
	}
	.detail .supports .support-item{
		padding: 0 12px;
		line-height:12px; 
		margin-bottom: 12px;
		color: rgb(255,255,255);
		font-size: 12px;
		font-weight: 200;
		text-align: left;
	}
	.detail .supports .support-item .icon{
		display: inline-block;
		height: 16px;
		width: 16px;
		vertical-align: top;
		background-size: 16px;
	}
	.support-item .decrease{
		background-image:url(decrease_2@2x.png);
	}
 	.support-item  .discount{
		background-image:url(discount_2@2x.png);
	}
	.support-item .special{
		background-image:url(special_2@2x.png);
	}
	.support-item .invoice{
		background-image:url(invoice_2@2x.png);
	}
	.support-item .guarantee{
		background-image:url(guarantee_2@2x.png);
	}	
	.bulletin{
		width: 80%;
		margin: 0 auto;
	}
	.bulletin .content{
		font-size: 12px;
		font-weight: 200;
		color: rgb(255,255,255);
		line-height: 24px;
		text-align: left;
	}
	.detail .detail-close .icon-close{
		font-size: 32px;
		color: rgba(255,255,255,0.5);
	}
	.support-count .icon-keyboard_arrow_right{
		font-size: 10px;
		color: #fff;
	}
</style>
