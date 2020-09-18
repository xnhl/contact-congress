<script>
import { Bar } from 'vue-chartjs'
export default {
	extends: Bar,
	data() {
		return {
			options: {
				responsive: true,
				tooltips: {
					bodyFontSize: 20,
					callbacks: {
						label: function(tooltipItem, data) {
							var label = data.labels[tooltipItem.index] + ': '
							var amount = (data.datasets[tooltipItem.datasetIndex].data[tooltipItem.index])
							var formatter = new Intl.NumberFormat('en-US', {
								style: 'currency',
								currency: 'USD',
								minimumFractionDigits: 0
							})
							label += formatter.format(amount)
							return label
						},
						labelTextColor: function(tooltipItem, chart){
							return '#fff'
						}
					}
				},
				legend: {
					display: false,
				},
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
						stacked: true,
						gridLines: {
							color: 'rgba(0, 0, 0, 0.25)'
						},
						ticks: {
							fontColor: 'black',
							padding: 5,
							stepSize: 2500000,
							callback: function(value, index, values) {
								return value.toLocaleString("en-US",{style:"currency", currency:"USD", minimumFractionDigits: 0, maximumFractionDigits: 0})
							}
						}
					}]
				},
				cutoutPercentage: 50,
			}
		}
	},
	computed: {
		chartdata: function() {
			return {
				labels: ["AT&T", "Comcast", "Verizon"],
				datasets: [{
					backgroundColor: ['rgba(0, 167, 220, 0.75)', 'rgba(0, 178, 86, 0.75)', 'rgba(221, 28, 17, 0.75)'],
					hoverBackgroundColor: ['rgba(0, 167, 220, 1)', 'rgba(0, 178, 86, 1)', 'rgba(221, 28, 17, 1)'],
					borderColor: 'rgba(255, 255, 255, 0.5)',
					borderWidth: 1.25,
					borderAlign: 'inner',
					data: [19836019, 14899570, 11240950]
				}]
			}
		}
	},
	mounted () {
		this.renderChart(this.chartdata, this.options)
	}
}
</script>
