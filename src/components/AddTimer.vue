<template>
	<div class="addTimer">
		<span class="rotate"/>
		<span/>
	</div>
</template>

<script>
	export default {
		name:"add-timer",
	}
</script>

<style lang="scss" scoped>
	.addTimer{
		position: relative;
		width:225px;
		height:120px;
		background: #696969;
		cursor: pointer;

		span{
			position: absolute;
			width: 20px;
			height: 3px;
			left: 50%;
			top: 50%;
			position: absolute;
			background: #9e9e9e;	
			transform:translate(-50%);
			}
		.rotate{
			transform: rotate(-90deg) translateY(-10px);
		}	
	}
</style>