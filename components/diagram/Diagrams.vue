<template>
	<div class="diagrams">
		<DiagramBar :data="data1" />
		<DiagramBar :data="data2" />
	</div>
</template>

<script>

export default {
	setup() {
		
	},
	data() {
		return {
			data1: {
				title: 'Посещаемость за день',
				arr1: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
				arr2: [0.2, 0.5, 1, 2, 2, 3, 4, 5.5, 7.5, 10],
				labels: [ '8:00 AM', '9:00 AM', '10:00 AM', '11:00 AM', '12:00 AM', '1:00 PM', '2:00 PM', '3:00 PM', '4:00 PM', '5:00 PM' ],
			},
			data2: {
				title: 'Оценка сотрудника в течении месяца',
				arr1: [
					{'x': 1, 'y': 1},
					{'x': 4, 'y': 2},
					{'x': 7, 'y': 3},
					{'x': 10, 'y': 4},
					{'x': 13, 'y': 5},
					{'x': 16, 'y': 6},
					{'x': 19, 'y': 7},
					{'x': 23, 'y': 8},
					{'x': 27, 'y': 9},
					{'x': 31, 'y': 10},
				],
				arr2: [
					{'x': 1, 'y': 0.1},
					{'x': 4, 'y': 0.2},
					{'x': 7, 'y': 1},
					{'x': 10, 'y': 2},
					{'x': 13, 'y': 2},
					{'x': 16, 'y': 3},
					{'x': 19, 'y': 4},
					{'x': 23, 'y': 5},
					{'x': 27, 'y': 7},
					{'x': 31, 'y': 10},
				],
				labels: [1, 4, 7, 10, 13, 16, 19, 23, 27, 31]
			}
			
			
		}
	}
}
</script>

<style lang="scss">
	.diagrams {
		width: 90%;
		height: 70%;
		display: flex;
		flex-wrap: wrap;
		flex-direction: row;
		gap: 25px;
	}
</style>