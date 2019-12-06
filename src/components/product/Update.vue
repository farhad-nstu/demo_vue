<template>
	<div class="row">
		<div class="container" style="border: 2px solid green;">
			<div class="col-md-8 col-md-offset-2">
				<div class="panel panel-default">
					<div class="panel-body">
						<div class="form-group">
							<label>Product Name</label>
							<input type="text" class="form-control" v-model="product.name">
						</div>
						<div class="form-group">
							<label>Product Price</label>
							<input type="number" class="form-control" v-model="product.price">
						</div>
						<div class="form-group">
							<label>Product Description</label>
							<textarea type="text" class="form-control" v-model="product.description"></textarea>
						</div>
						<button class="btn btn-success pul-right" v-show="product.name && product.price && product.description" @click="update">
						   Update
						</button>
					</div>
				</div>
			</div>	
		</div>	    
	</div>
</template>

<script>

import swal from 'sweetalert'

	export default {

		created() {
			this.getProduct()
		},

		data() {
			return {
				product: {}
			}
		},

		methods: {

			getProduct() {
				this.$http.get('api/products/' + this.$route.params.product)
				.then(response => {
					this.product = response.body
				})

				/*.catch(response => {
					swal(response.status, response.body.error, "error")
				})*/
			},

			update () {
				this.$http.put('api/products/' + this.$route.params.product, this.product)
				.then(response => {
					
					swal("Updated!", "Your Product Has Been Updated!", "success")
					this.$router.push('/feed')
				})
			}
		}
	}
</script>