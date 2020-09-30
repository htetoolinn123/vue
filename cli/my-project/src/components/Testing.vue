<template>
	<div >
		<h1 class="text-danger text-center">Bitcoin Price Index</h1>
		<!-- <p>{{name}}</p> -->
		<!-- <button @click="showData">Show Data</button> -->
		<div class="text-center" >
			<p v-for="(row,index) in info " :key="index">{{row.description}}:<span v-html="row.symbol">{{row.symbol}}</span>{{row.rate_float|currencydecimal}}</p>
		</div>
	</div>
</template>

<script type="text/javascript">
	export default{
		data(){
			return{
				name:'Htet Oo Linn',
				info:null
			}
		},
		mounted(){
			this.showData();
		},
		methods:{
			showData(){
				this.$http.get('https://api.coindesk.com/v1/bpi/currentprice.json')
				.then(response=>{
					//console.log(response)
					this.info = response.data.bpi
				})
			}
		},
		filters:{
			currencydecimal(value){
				return value.toFixed(2)
			}
		}
	}
</script>

<style type="text/css">
	
</style>