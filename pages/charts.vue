<template>
	<div id="wrapper">
		<!-- <canvas id="test"></canvas> -->
		<!-- <MyChart type="pie" elid="testing" :data="gender" /> -->
		<!-- <p>{{chartData}}</p> -->
		<div id="charts">
			<!-- <p>Men and Women</p> -->
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
			<!-- <FirstChart :chartdata="chartData" :options="chartOptions" type="Doughnut" /> -->
		</div>
	</div>
</template>

<script>
// import Chart from 'chart.js'
// import FirstChart from '@/components/FirstChart'
import Genders from '@/components/Genders'
import Parties from '@/components/Parties'
import Ages from '@/components/Ages'
import NNVote from '@/components/NNVote'
import TelecomsOne from '@/components/TelecomsOne'
import TelecomsTwo from '@/components/TelecomsTwo'
import TopEarners from '@/components/TopEarners'
import reps from '@/assets/data/currentMin'
// import reps from '@/assets/newerData/allNew25Min'
// import axios from '~/plugins/axios'
export default {
	// async asyncData() {
		// let newColor = document.documentElement;
		// let styles = newColor.style.getPropertyValue('--test-var');
		// return {vcolor: styles}
	//   let { data } = await axios.get('/api/visuals');
	//   return { gender: data }
	// },
	components: {Genders, Ages, Parties, NNVote, TelecomsOne, TelecomsTwo, TopEarners},
	data() {
		return {
			representatives: reps,
		}
	},
	// computed: {
		// chartData: function() {
		//   // let genders = ;
		//   let males = 0
		//   let females = 0;
		//   // let len = this.representatives.length;
		//   // for (let i = 0; i < len; i++) {
		//   //   if (this.representatives[i].gender === "M") {males++} else if (this.representatives[i].gender === "F") {females++}
		//   // }
		//   // return `Men: ${males}, Women: ${females}`
		//   this.representatives.forEach(rep => {
		//     if (rep.gender === "M") {males++} else if (rep.gender === "F") {females++}
		//   });
		//   // const reducer = (accumulator, rep) => accumulator + rep;
		//   // const reducer = (accumulator, rep) => accumulator += rep.gender == "M" ? 1 : 0;
		//   // let males = this.representatives.reduce((accumulator, rep) => {return accumulator += rep.gender == "M" ? 1 : 0});
		//   // let females = this.representatives.reduce((accumulator, rep) => {return accumulator += rep.gender == "F" ? 1 : 0});
		//   return {
		//     // counts: {
		//     //   males, females
		//     // }
		//     labels: ['Males', 'Females'],
		//     datasets: [
		//       {
		//         label: 'Data One',
		//         backgroundColor: ['blue', 'pink'],
		//         data: [males, females]
		//       }
		//     ]
		//   }
		// },
		// chartOptions: function() {
		//   return {
		//     responsive: true,
		//     cutoutPercentage: 50
		//   }
		// }
		// gender: function() {
		//   return this.reps.map(rep => {
		//     return rep.gender
		//   })
		// }
	// },
	// methods: {
		// createChart(chartId, chartData) {
		//   const ctx = document.getElementById(chartId);
		//   const myChart = new Chart(ctx, {
		//     type: "pie",
		//     data: reps,
		//     options: {},
		//   });
		// }
	// },
	// mounted() {
		// let newColor = document.body;
		// let styles = newColor.style.getPropertyValue('--test-var');
		// console.log(styles)
		// this.createChart('test', this.gender);
		// console.log(this.chartData)
	// }
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
			// border: 0.1rem solid rgba(white, 0.5)
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
				// font-size: 0.75rem
				text-align: left
				text-indent: 0.25rem
				margin-bottom: 1rem
			.chart-source
				@include flexCenter
				justify-content: flex-end
				// padding: 0.25rem
				min-width: 100%
				margin-top: 1.5rem
				// color: rgba(white, 0.5)
				font-size: 0.75rem
				// text-align: right
</style>
