<template>
	<div class="row">
		<my-product v-for="product in products" :product="product" :authenticatedUser="authenticatedUser"></my-product>
        
	</div>
</template>

<script>

	import Product from './Product.vue'

	export default {
		data() {
			return {
				products: []
			}
		},

		computed: {
			authenticatedUser () {
				return this.$auth.getAuthenticatedUser()
			}
		}, // if we put this authenticatedUser in data then we do not get the user after refreshing. so we put this in the computed.

		components: {
			'my-product': Product
		},

		created() {
           this.$http.get('api/products')
           .then(response => {
           	   this.products = response.body
           })
		}
	}
</script>