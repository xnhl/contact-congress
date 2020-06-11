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
			let yes = 0
			let no = 0;
			let unknown = 0;
			this.reps.forEach(rep => {
				if (rep.nn_vote === "yes") {yes++} else if (rep.nn_vote === "no") {no++} else unknown++
			});
			return {
				labels: ['Yes', 'No', 'Unknown'],
				datasets: [
					{
						label: 'Vote',
						borderWidth: 1.25,
						borderAlign: 'inner',
						borderColor: 'rgba(255, 255, 255, 0.5)',
						backgroundColor: ['green', 'red', 'gray'],
						data: [yes, no, unknown]
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
