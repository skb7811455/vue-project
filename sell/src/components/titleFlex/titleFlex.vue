<template>
	<div class="titleFlex">
		<div class="line"></div>
		<div class="text">{{text}}</div>
		<div class="line"></div>
	</div>
</template>

<script>
	export default {
		props:{
			text:{
				type:String
			}
		}
	};
</script>

<style>
	.titleFlex{
		display: flex;
		width: 80%;
		margin: 28px auto 24px auto;
	}
	.titleFlex .line{
		flex:1;
		border-bottom: 1px solid rgba(255,255,255,0.2);
		position: relative;
		top:-6px;
	}
	.titleFlex .text{
		padding: 0 12px 0 12px;	
		font-size: 14px;
		font-weight: 700;
		color: rgb(255,255,255);
		line-height: 14px;
	}
</style>