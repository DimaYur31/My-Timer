<template>	
	<main>
		<div class="timerList">
			<Timer v-for="timer in timerList" :key="timer"/>
			<AddTimer @click="addTimer"/>
		</div>
	</main>
</template>

<script>
	import Timer from "./components/Timer.vue"
	import AddTimer from "./components/AddTimer.vue"

	export default {
		name: "App",
		
		components: {
			Timer, AddTimer
		},

		data(){
			return{
				timerList:[]
			}
		},

		methods:{
			addTimer(){
				this.timerList.push(Date.now())
			}
		}
	}
</script>

<style lang="scss">
@font-face {
	font-family: "Gotham Pro";
	src: url(./assets/gothampro.ttf);
}

* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}

body{
	background-color: #353638;
	margin: 0 auto;
}

main{
	display: flex;
	justify-content: center;
	padding: 72px 0px 82px 0px;
}

.timerList{
	display: grid;
	grid-template-columns: 225px;
	grid-row-gap: 45px;
}

@media(min-width:768px){
	.timerList{
		grid-template-columns: repeat(2,225px);
		grid-column-gap: 50px;
	}
}

@media(min-width:1024px){
	.timerList{
		grid-template-columns: repeat(3,225px);
		grid-column-gap: 50px;
	}
}
</style>
