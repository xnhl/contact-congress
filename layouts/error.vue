<template>
	<section id="error-wrapper">
		<section id="error-content">
			<p class="error-code">{{ error.statusCode }}</p>
			<p class="info">Page does not exist.</p>
			<p class="info">Going back...</p>
		</section>
	</section>
</template>

<script>
export default {
	props: ['error'],
	mounted() {
		setTimeout(() => {
			this.$router.go(-1)
		}, 1000)
	}
}
</script>

<style lang="sass">
#error-wrapper
	@include flexCenter
	margin: 0 auto
	min-height: 100vh
	padding: 0.5rem
	color: white
	animation: fadeIn 0.3s
	@media (min-width: 40rem)
		padding: 1rem
	#error-content
		@include flexCenter
		flex-direction: column
		.error-code
			font-size: 5rem
			color: darken(white, 50)
		.info
			font-size: 1.5rem
</style>
