<script>
import { Bar } from 'vue-chartjs'
export default {
	/* eslint-disable */
	extends: Bar,
	data() {
		return {
			data: {
				labels: ["John McCain", "Steny H. Hoyer", "Fred Upton"],
					datasets: [{
						label: '',
						borderAlign: 'inner',
						backgroundColor: ['rgba(0, 167, 220, 0.75)', 'rgba(0, 178, 86, 0.75)', 'rgba(221, 28, 17, 0.75)'],
						hoverBackgroundColor: ['rgba(0, 167, 220, 1)', 'rgba(0, 178, 86, 1)', 'rgba(221, 28, 17, 1)'],
						borderColor: 'rgba(255, 255, 255, 0.5)',
						borderWidth: 1.25,
						data: [794881, 659490, 631000]
					}]
			},
			options: {
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
							stepSize: 100000,
							callback: function(value, index, values) {
								return value.toLocaleString("en-US",{style:"currency", currency:"USD", minimumFractionDigits: 0, maximumFractionDigits: 0});
							}
						}
					}]
				},
				tooltips: {
					bodyFontSize: 20,
					callbacks: {
						label: function(tooltipItem, data) {
							var label = data.labels[tooltipItem.index] + ': ';
							var amount = data.datasets[tooltipItem.datasetIndex].data[tooltipItem.index];
							var formatter = new Intl.NumberFormat('en-US', {
								style: 'currency',
								currency: 'USD',
								minimumFractionDigits: 0
							});
							label += formatter.format(amount);
							return label;
						}
					}
				},
				legend: {
					display: false,
					labels: {
						fontColor: 'black',
						fontSize: 24,
						padding: 10
					}
				},
				title: {
					display: false,
					fontSize: 24,
					padding: 10,
					fontColor: 'black',
					text: 'Top Earners'
				}
			}
		}
	},
	mounted () {
		this.renderChart(this.data, this.options)
	}
}
</script>
