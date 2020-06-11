<script>
import { Doughnut } from 'vue-chartjs'
export default {
	extends: Doughnut,
	data() {
		return {
			options: {
				responsive: true,
				tooltips: {
					bodyFontSize: 20,
					callbacks: {
						label: function(tooltipItem, data) {
							var label = data.labels[tooltipItem.index] + ': ';
							var amount = (data.datasets[tooltipItem.datasetIndex].data[tooltipItem.index]);
							var formatter = new Intl.NumberFormat('en-US', {
								style: 'currency',
								currency: 'USD',
								minimumFractionDigits: 0
							});
							label += formatter.format(amount);
							return label;
						},
						labelTextColor: function(tooltipItem, chart){
							return '#fff';
						}
					}
				},
				legend: {
					labels: {
						fontColor: 'black',
						padding: 10
					}
				},
				cutoutPercentage: 50,
			}
		}
	},
	computed: {
		chartdata: function() {
			return {
				labels: ["Republicans", "Democrats", "Independents"],
				datasets: [{
					backgroundColor: ['rgba(241, 11, 22, 0.75)', 'rgba(0, 173, 239, 0.75)', 'rgba(132, 0, 123, 0.75)'],
					hoverBackgroundColor: ['rgba(241, 11, 22, 1)', 'rgba(0, 173, 239, 1)', 'rgba(132, 0, 123, 1)'],
					borderColor: 'rgba(255, 255, 255, 0.5)',
					borderWidth: 1.25,
					borderAlign: 'inner',
					data: [55805224, 45044252, 150524]
				}]
			}
		}
	},
	mounted () {
		this.renderChart(this.chartdata, this.options)
	}
}
</script>
