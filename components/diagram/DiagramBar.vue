<template>
	<div class="diagram">
		<Bar
			id="my-chart-id"
			:options="chartOptions"
			:data="chartData"
		/>
	</div>
	
</template>

<script>
import { Bar } from 'vue-chartjs'

import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
	components: { 
		Bar,
	},
	setup() {
		
	},
	data() {
		return {
			
		}
	},
	props: {
		data: Object,
	},
	computed: {
		chartOptions() {
			return {
				responsive: true,
				plugins: {
					title: {
						display: true,
						text: this.data.title
					},
					
				}
			}
		},
		chartData() {
			return {
				labels: this.data.labels,
				datasets: [ 
					{ 
						barPercentage: 1,
						label: 'Январь',
						data: this.data.arr1 ,
						backgroundColor: 'rgb(51, 102, 204)'
					},
					{ 
						barPercentage: 1,
						label: 'Декабрь',
						data: this.data.arr2 ,
						backgroundColor: 'rgb(220, 57, 18)'

					}
				]
			}
		}
	}

}
</script>

<style lang="scss">
.diagram {
	width: 45%;
	height: 45%;
}
</style>