<template>
	<div class="finance-item" :style="`background: ${bg};`">
		<div class="finance-item__content">
			<input type="checkbox" name="" id="" class="finance-item__checkbox">
			<p class="finance-item__text">{{ date }}</p>
			<p class="finance-item__text">{{ opType }}</p>
			<p class="finance-item__text">{{ price }}</p>
			<p class="finance-item__text">{{ employe }}</p>
			<p class="finance-item__text">{{  description }}</p>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			date: this.item.date,
			opType: this.item.opType,
			price: this.item.price,
			employe: this.item.employe,
			description: this.item.description,
		}
	},
	props: {
		item: Object,
		bg: String
	},
	setup() {
		
	},
}
</script>

<style lang="scss">
.finance-item {
	padding: 15px 21px;
	box-sizing: border-box;
	

	&__content {
		display: grid;
		grid-template-columns: 1fr 3fr 4fr 4fr 5fr 12fr;
	}

	&__checkbox {
		background: #B8B8B8;
		margin: 0;
		padding: 0;
		border: 0;
		border-radius: 5px;
		width: 23px;
		height: 23px;
	}

	&__text {

		margin: 0;
		font-family: Gilroy;
		font-size: 16px;
		font-weight: 400;

		text-align: center;
	}
}

</style>