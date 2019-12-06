<template>

	<div class="col-md-4">
		<div class="container">
			
			<div style="border: 2px solid green; background-color: blue;">
				<img src="images/1.jpg" style="" class="pull-right">
				<h5 style="color: #fff;">User Id: {{ product.user_id }}</h5>
				<h3 style="color: white; padding-left: 5px;">{{ product.name }}</h3>
				<p style="color: white; padding-left: 5px;">{{ product.price }}</p>

				<hr>

				<p>
					<button href="#" class="btn btn-success">Interest</button>
				<button href="#" class="btn btn-success">Buy</button>
				</p>
				<hr>
					<p v-if="product.user_id == authenticatedUser.id">
						<a href="#" class="btn btn-sm btn-danger" role="button">Delete</a>
					</p>

					<router-link class="btn btn-sm btn-success" :to="'/products/' + product.id + '/update'">Edit</router-link>
				
			</div>
		</div>
	</div>
</template>

<script>
	import swal from 'sweetalert'
	export default {
		props: ['product', 'authenticatedUser'],

		methods: {
			/*deleteProduct () {
				swal({
					 title: "Good job!",
					 text: "You clicked the button!",
					 icon: "success",
					 type: "warning",
					 showCancelButton: true,
					 confirmButtonColor: "#DD6B55",
					 confirmButtonText: "Yes, delete it!",
					 closeConfirm: false
				},

					function(){
						alert()
						this.$http.delete('api/products/' + this.product.id)
						.then(response => {
							console.log(response)
						})
					}.bind(this)
                );
                
				
			}*/
		}
	}
</script>