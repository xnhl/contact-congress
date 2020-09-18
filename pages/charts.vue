<template>
	<div id="wrapper">
		<div id="charts">
			<div class="chart">
				<p class="chart-title">Gender</p>
				<p class="chart-subtitle"></p>
				<Genders />
				<p class="chart-source">Source: ProPublica</p>
			</div>
			<div class="chart">
				<p class="chart-title">Age</p>
				<p class="chart-subtitle"></p>
				<Ages />
				<p class="chart-source">Source: ProPublica</p>
			</div>
			<div class="chart">
				<p class="chart-title">Party</p>
				<p class="chart-subtitle"></p>
				<Parties />
				<p class="chart-source">Source: ProPublica</p>
			</div>
			<div class="chart">
				<p class="chart-title">Net Neutrality</p>
				<p class="chart-subtitle"></p>
				<NNVote />
				<p class="chart-source">Source: Battle for the Net</p>
			</div>
			<div class="chart">
				<p class="chart-title">$101 Million</p>
				<p class="chart-subtitle">Lifetime contributions from the telecommunications industry to sitting members of Congress and their leadership PACs, between 1989 and 2017, consolidated by party.</p>
				<TelecomsOne />
				<p class="chart-source">Source: The Center for Responsive Politics</p>
			</div>
			<div class="chart">
				<p class="chart-title">The Big Three</p>
				<p class="chart-subtitle">Contributions from AT&T, Comcast, and Verizon to sitting members of Congress and their leadership PACs, between 1989 and 2017.</p>
				<p class="chart-subtitle"></p>
				<TelecomsTwo />
				<p class="chart-source">Source: The Center for Responsive Politics</p>
			</div>
			<div class="chart">
				<p class="chart-title">Top Earners for Telecoms Companies (2017)</p>
				<p class="chart-subtitle"></p>
				<TopEarners />
				<p class="chart-source">Source: The Center for Responsive Politics</p>
			</div>
		</div>
	</div>
</template>

<script>
import Genders from '@/components/Genders'
import Parties from '@/components/Parties'
import Ages from '@/components/Ages'
import NNVote from '@/components/NNVote'
import TelecomsOne from '@/components/TelecomsOne'
import TelecomsTwo from '@/components/TelecomsTwo'
import TopEarners from '@/components/TopEarners'
import reps from '@/assets/data/currentMin'
export default {
	components: {Genders, Ages, Parties, NNVote, TelecomsOne, TelecomsTwo, TopEarners},
	data() {
		return {
			representatives: reps,
		}
	}
}
</script>

<style lang="sass">
#wrapper
	@include pageWrapper
	#charts
		@include flexCenter
		align-items: stretch
		.chart
			@include flexCenter
			flex: 1
			padding: 0.5rem
			margin: 1rem
			border-radius: 0.25rem
			max-width: 55%
			background: var(--theme-itemWhite)
			box-shadow: var(--theme-boxShadow)
			.chart-title
				@include flexCenter
				padding: 1rem
				margin-bottom: 1
				min-width: 100%
				font-size: 1.25rem
				text-align: center
			.chart-subtitle
				@include flexCenter
				padding: 0.25rem
				width: 100%
				max-width: 75%
				text-align: left
				text-indent: 0.25rem
				margin-bottom: 1rem
			.chart-source
				@include flexCenter
				justify-content: flex-end
				min-width: 100%
				margin-top: 1.5rem
				font-size: 0.75rem
</style>
