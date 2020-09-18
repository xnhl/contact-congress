<script>
import { Bar } from 'vue-chartjs'
import reps from '@/assets/data/currentMin'
export default {
	extends: Bar,
	data() {
		return {
			reps,
			options: {
				responsive: true,
				scales: {
					xAxes: [{
						display: true,
						gridLines: {
							color: 'rgba(0, 0, 0, 0.25)'
						},
						ticks: {
							fontColor: 'black',
							padding: 5
						}
					}],
					yAxes: [{
						display: true,
						gridLines: {
							color: 'rgba(0, 0, 0, 0.25)'
						},
						ticks: {
							fontColor: 'black',
							padding: 5,
							stepSize: 10
						}
					}]
				},
				legend: {
					display: false,
					labels: {
						fontColor: 'black',
						fontSize: 24,
						padding: 10
					}
				}
			}
		}
	},
	computed: {
		chartdata: function() {
			const moment = require('moment')
			const today = moment()
			let ages = [0, 0, 0, 0, 0, 0]
			this.reps.forEach(rep => {
				const bday = moment(rep.date_of_birth)
				const difference = today.diff(bday, 'years')
				if (difference >= 30 && difference < 40) {
					ages[0]++
				} else if (difference >= 40 && difference < 50) {
					ages[1]++
				} else if (difference >= 50 && difference < 60) {
					ages[2]++
				} else if (difference >= 60 && difference < 70) {
					ages[3]++
				} else if (difference >= 70 && difference < 80) {
					ages[4]++
				} else if (difference >= 80) {
					ages[5]++
				}
			})
			return {
				labels: ['30-40', '40-50', '50-60', '60-70', '70-80', '80+'],
				datasets: [
					{
						label: 'Number',
						borderWidth: 1.25,
						borderAlign: 'inner',
						borderColor: 'rgba(255, 255, 255, 0.5)',
						backgroundColor: ['rgba(255, 0, 0, 0.75)', 'rgba(255, 165, 0, 0.75)', 'rgba(255, 255, 0, 0.75)', 'rgba(0, 128, 0, 0.75)', 'rgba(0, 0, 255, 0.75)', 'rgba(128, 0, 128, 0.75)'],
						hoverBackgroundColor: ['rgba(255, 0, 0, 1)', 'rgba(255, 165, 0, 1)', 'rgba(255, 255, 0, 1)', 'rgba(0, 128, 0, 1)', 'rgba(0, 0, 255, 1)', 'rgba(128, 0, 128, 1)'],
						data: ages
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
