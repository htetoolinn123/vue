<template>
	<div >
		<div class="container">
		<h1 class="text-danger text-center">All Item Lists</h1>
		<div class="row">
			<div class="col-md-4" v-for="(row,index) in items" :key="index">
				<div>
					<b-card
					:title="row.item_name"
					:img-src="row.item_photo"
					img-alt="Image"
					img-top
					tag="article"
					style="max-width: 20rem;"
					class="mb-2"
					>
					<b-card-text>
						{{row.item_desc}}
					</b-card-text>

					<b-button href="#" variant="primary">Go somewhere</b-button>
				</b-card>
			</div>
		</div>
	</div>
</div>
</div>
</template>

<script type="text/javascript">
	export default{
		data(){
			return{
				name:'Htet Oo Linn',
				items:[]
			}
		},
		mounted(){
			this.getData();
		},
		methods:{
			getData(){
				this.$http.get('http://osapi.thetpainghtut.com/api/v1/items')
				.then(response=>{
					console.log(response)
					this.items = response.data.items
				})
			}
		},
		filters:{
			// currencydecimal(value){
			// 	return value.toFixed(2)
			// }
		}
	}
</script>

<style type="text/css">

</style>