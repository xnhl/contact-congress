<script>
import { Doughnut } from 'vue-chartjs'
import reps from '@/assets/data/currentMin'
export default {
	extends: Doughnut,
	data() {
		return {
			reps,
			options: {
				responsive: true,
				cutoutPercentage: 50,
				legend: {
					labels: {
						fontColor: 'black',
						padding: 10
					}
				}
			}
		}
	},
	computed: {
		chartdata: function() {
			let dems = 0
			let repubs = 0
			let inde = 0
			this.reps.forEach(rep => {
				if (rep.party === "D") {dems++} else if (rep.party === "R") {repubs++} else {inde++}
			})
			return {
				labels: ['Democrats', 'Republicans', 'Independent'],
				datasets: [
					{
						label: 'Party',
						borderWidth: 1.25,
						borderAlign: 'inner',
						borderColor: 'rgba(255, 255, 255, 0.5)',
						backgroundColor: ['blue', 'red', 'purple'],
						data: [dems, repubs, inde]
					}
				]
			}
		}
	},
	mounted () {
		this.renderChart(this.chartdata, this.options)
	}
}
</script>
