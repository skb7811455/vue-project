<template>
	<div class="star" :class="starType">
		<span v-for="item in itemClass" :class="item" class="star-item"></span>
	</div>
</template>

<script>
	const LENGTH=5;
	const ON="on";
	const HALF="half";
	const OFF="off";

	export default {
		props:{
			size:{
				type:Number
			},
			score: {
				type:Number
			}
		},
		computed:{
			starType(){
				return "star-"+this.size;
			},
			itemClass(){
				let result=[];
				let score=Math.floor(this.score*2)/2;
				let hasDeceil=score%1;
				let inter=Math.floor(score);
				let j=inter;			
					for(let i=0;i<inter;i++){
						result[i]=ON;
					}
					if(hasDeceil) {result.push(HALF);j++}
					while(j<LENGTH){
						result.push(OFF);	
						j++;				
					}		
				return result;			
			}
		}
	};
</script>

<style>
	.star{
		font-size: 0;
	}
	.star-item{
		display: inline-block;
	}
	.star-48{
		padding: 0 10% 0 17%;
	}
	.star-48 .star-item{
		width: 20px;
		height: 20px;
		margin-right: 22px;
		background-size: 20px 20px;
	}
	.star-48 .on{
		background-image: url(star48_on@2x.png);
	}
	.star-48 .half{
		background-image: url(star48_half@2x.png);
	}
	.star-48 .off{
		background-image: url(star48_off@2x.png);
	}
	.star-36 .star-item{
		width: 15px;
		height: 15px;
		margin-right: 6px;
		background-size: 15px 15px;
	}
	.star-36 .on{
		background-image: url(star36_on@2x.png);
	}
	.star-36 .half{
		background-image: url(star36_half@2x.png);
	}
	.star-36 .off{
		background-image: url(star36_off@2x.png);
	}
	.star-24 .star-item{
		width: 10px;
		height: 10px;
		margin-right: 3px;
		background-size: 10px 10px;
	}
	.star-24 .on{
		background-image: url(star24_on@2x.png);
	}
	.star-24 .half{
		background-image: url(star24_half@2x.png);
	}
    .star-24 .off{
		background-image: url(star24_off@2x.png);
	}
</style>