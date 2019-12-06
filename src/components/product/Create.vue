<template>
	<div class="row">
		<div class="container" style="border: 2px solid green;">
			<div class="col-md-8 col-md-offset-2">
				<div class="panel panel-default">
					<div class="panel-body">
						<div class="form-group">
							<label>Product Name</label>
							<input type="text" name="name" class="form-control" v-model="product.name">							
						</div>
						<div class="form-group">
							<label>Product Price</label>
							<input type="number" class="form-control" v-model="product.price">
						</div>
						<div class="form-group">
							<label>Product Description</label>
							<textarea type="text" class="form-control" v-model="product.description"></textarea>
						</div>
						<div class="form-group">
							<label>Product Photo</label>
							<input type="file" class="form-control" @change="imageChanged">							
						</div>
						<button class="btn btn-success pul-right" v-show="product.name && product.price && product.description" @click="create">
						   Save
						</button>
					</div>
				</div>
			</div>	
		</div>	    
	</div>
</template>

<script>



	export default {
		

		data() {
			return {
				product: {
					name: '',
					price: 0,
					description: '',
					file: ''
				}
			}
		},

		methods: {

			/*imageChanged (e) {
				console.log(e.target.files[0])
                var fileReader = new FileReader()

                fileReader.readAsDataURL(e.target.files[0])

                fileReader.onlaod = (e) => {
                	this.product.image = e.target.result
                }
                console.log(this.product)
			},*/

			imageChanged (e) {
				var reader = new FileReader();

			reader.onload = function(e) {
			  var text = reader.result;
			}

			reader.readAsText(file, encoding);
			
			},

			

			create () {
				this.$http.post('api/products', this.product)
				.then(response => {
					this.$router.push('/feed')
				})
			}


		}
	}
</script>