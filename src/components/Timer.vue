<template>
	<div v-bind:class="['timer', isPlayed?'active':'']" >
		<div class="screen">
			<span v-if="hours > 0">{{hours}}:</span>
			<span v-if="hours > 0 || minutes > 0">{{minutes}}:</span>
			<span>{{seconds}}</span>
		</div>
		<div class="buttons">
			<span
			v-if="!isPlayed"
				class="startBtn"
				@click="startStopTimer"
			/>
			<span
			v-else
				class="stopBtn"
				@click="startStopTimer"
			/>
			<span
			class="clearBtn"
				@click="clearTimer"
			/>
		</div>
		
	</div>
</template>

<script>
	export default {
		name:"my-timer",

		data(){
			return {
				seconds: 0,
				minutes: 0,
				hours: 0,
				isPlayed:false,
				interval: null
			}
		},

		methods:{
			start(){
				this.interval = 	setInterval(this.incrementTime,1000)
			},

			stop(){
				clearInterval(this.interval)
			},
		
			incrementTime(){
				this.seconds++
			},

			startStopTimer(){			
				this.isPlayed = !this.isPlayed
			},

			clearTimer(){
				this.seconds = 0
				this.minutes =0
				this.hours= 0
				this.isPlayed=false
			},
		},

		watch:{
			seconds(){
				if(this.seconds > 59){
					this.seconds = 0
					this.minutes++
				}
			},
			minutes(){
				if(this.minutes > 59){
					this.minutes = 0
					this.hours++
				}
			},
			hours(){
				if(this.minutes > 59){
					this.hours++
				}
			},
			isPlayed(){
				if(this.isPlayed){
					this.start()
				}else{
					this.stop()
				}
			}
		}		
	}
</script>

<style lang="scss" scoped>
.timer{
	font-family: "Gotham Pro";
	position: relative;
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	background: #696969;
	width:225px;
	height:120px;

	&.active{
			.screen{
				color:#fff;
				border-color:#fff;
			}

		.clearBtn{
			background:#fff;
		}
		
		.stopBtn{
			&::before,
			&::after{
				background:#fff;
			}
		}
	}	
	
	.screen,
	.buttons{
		
		display: flex;
		position: relative;
		align-items: center;
		justify-content: center;
		height: 50%;
		width: 100%;
	}

	.screen{
		border-bottom: 1px solid#9E9E9E;
		font-size: 22px;
		color:#9E9E9E;	
	}
	
	.buttons{
		gap:46.5px
	}

	.clearBtn{
		position: relative;
		width: 20px;
		height: 20px;
		background:#9e9e9e;
		cursor:pointer;
	}

	.startBtn{
		position: relative;
		display: flex;
		justify-content: center;
		width: 20px;
		height: 20px;
		cursor: pointer;

		&::before{
			content: "";
			position: relative;
			width: 0;
			height: 0;
			border-style: solid;
			border-width: 10px 0 10px 17px;
			border-color: transparent transparent transparent #9e9e9e;
			
		}
	}

	.stopBtn{
		position: relative;
		width: 20px;
		height: 20px;
		background: #696969;
		display: flex;
		justify-content: center;
		gap:4px;

		&::before,
		&::after{
			content: "";
			position: relative;
			height: 100%;
			width: 3px;
			background: #9e9e9e;
		}
	}
}
</style>