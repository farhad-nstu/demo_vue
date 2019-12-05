<template>

	<div class="col-md-4">
		<div class="container">
			
			<div style="border: 2px solid green; background-color: blue;">
				<img src="images/1.jpg" style="" class="pull-right">
				{{ product.user_id }}
				<h3 style="color: white; padding-left: 5px;">{{ product.name }}</h3>
				<p style="color: white; padding-left: 5px;">{{ product.price }}</p>

				<hr>

				<p>
					<button href="#" class="btn btn-success">Interest</button>
				<button href="#" class="btn btn-success">Buy</button>
				</p>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		props: ['product']
	}
</script>