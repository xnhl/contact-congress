<template>
	<div id="navigation">
		<div id="nav-list">
			<nuxt-link class="nav-list-item" to="/" exact active-class="active">
			<img src="/icons/home.svg" alt="home" class="nav-list-item-icon">
			</nuxt-link>
			<nuxt-link class="nav-list-item" to="/charts" active-class="active">
				<p class="nav-list-item-text">Charts</p>
			</nuxt-link>
		</div>
	</div>
</template>

<script>
export default {
	name: 'Navigation',
	data() {
		return {
			scroll_old: 0,
			scroll_new: 0
		}
	},
	methods: {
		handleScroll: function() {
			let y = window.scrollY
			this.scroll_new = y
			let nav_wrapper = document.getElementById("navigation")
			if (this.scroll_new > this.scroll_old) {
				nav_wrapper.classList.add("nav-hidden")
				this.scroll_old = y
			} else if (this.scroll_new < this.scroll_old) {
				nav_wrapper.classList.remove("nav-hidden")
				this.scroll_old = y
			}
		}
	},
	mounted() {
		window.addEventListener('scroll', this.handleScroll)
	}
}
</script>

<style lang="sass">
#navigation
	color: white
	position: fixed
	top: 0
	left: 0
	z-index: 3
	min-width: 100%
	@include flexCenter
	justify-content: flex-end
	background: var(--theme-whiteBG)
	transition: $transition
	&.nav-hidden
		top: -5rem
	#nav-list
		@include flexCenter
		align-items: stretch
		justify-content: flex-start
		width: 100%
		.nav-list-item
			color: white
			text-decoration: none
			color: var(--theme-black)
			@include flexCenter
			&:hover
				box-shadow: var(--theme-boxShadowHover)
			&.active
				box-shadow: var(--theme-boxShadow)
			.nav-list-item-text
				padding: 0.5rem
			.nav-list-item-icon
				height: 1.25rem
				width: 1.25rem
				cursor: pointer
				padding: 0.5rem
				filter: var(--theme-icon)
				box-sizing: content-box
</style>
