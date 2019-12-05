<template>

	<div>
		<h1 style="text-align: center;">All Products</h1>
		<my-products></my-products>
	</div>
	
</template>

<script>
	import Products from './product/Products.vue'
	export default {
		components: {
			'my-products': Products
		}
	}
</script>