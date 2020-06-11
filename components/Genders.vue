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
				},
				tooltips: {
					bodyFontSize: 20
				}
			}
		}
	},
	computed: {
		chartdata: function() {
			let males = 0
			let females = 0;
			this.reps.forEach(rep => {
				if (rep.gender === "M") {males++} else if (rep.gender === "F") {females++}
			});
			return {
				labels: ['Male', 'Female'],
				datasets: [
					{
						label: 'Gender',
						borderWidth: 1.25,
						borderAlign: 'inner',
						borderColor: 'rgba(255, 255, 255, 0.5)',
						backgroundColor: ['blue', 'pink'],
						data: [males, females]
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
