<template>
	<div id="wrapper">
		<Sorter />
		<div id="reps-wrapper">
			<Rep v-for="(rep, index) in congress" :class="{ 'lazyloading': index > 9 }" :key="index" :info="rep" />
		</div>
		<div id="trigger"></div>
	</div>
</template>

<script>
import Sorter from '@/components/Sorter'
import Rep from '@/components/Rep.vue'
import reps from '@/assets/data/currentMin'
export default {
	components: {Rep, Sorter},
	data() {
		return {
			congress: reps,
			offset: 1,
			num: 25
		}
	},
	methods: {
		showNext: function() {
			let reps = [...document.getElementsByClassName("representative")]
			let to_show = reps.slice(this.offset*this.num, (this.offset*this.num)+this.num)
			for (let rep of to_show) {
				rep.classList.remove("lazyloading")
			}
			this.offset++
		}
	},
	mounted() {
		var lazyloadImages = document.querySelectorAll('.lazy')
		var imageObserver = new IntersectionObserver((entries, observer) => {
			entries.forEach((entry) => {
				if (entry.isIntersecting) {
					var image = entry.target
					image.src = image.dataset.lazysrc
					image.classList.remove('lazy')
					imageObserver.unobserve(image)
				}
			})
		})
		lazyloadImages.forEach((image) => {
			imageObserver.observe(image)
		})
		var loader = document.querySelector('#trigger')
		var loadObserver = new IntersectionObserver((entries, observer) => {
			if (entries[0].isIntersecting) {
				this.showNext()
			}
			var imgArr = document.querySelectorAll('.lazy')
			imgArr.forEach((image) => {
				imageObserver.observe(image)
			})
		})
		loadObserver.observe(loader)
	}
}
</script>

<style lang="sass">
#wrapper
	@include pageWrapper
	#trigger
		min-height: 2vh
	#reps-wrapper
		width: 100%
		@include flexCenter
		align-items: stretch
		animation: fadeIn 0.25s
		.lazyloading
			display: none !important
</style>
