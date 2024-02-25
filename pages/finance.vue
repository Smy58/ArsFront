<template>
	<div class="finance-page">
		<FinanceAddPopup v-if="isPopup" :closePopup="switchPopup"/>
		<Finance :openPopup="switchPopup"/>
	</div>
</template>

<script>


export default {
	data() {
		return {
			isPopup: false,
		}
	},
	setup() {
		
	},
	computed: {

	},
	methods: {
		switchPopup() {
			this.isPopup = !this.isPopup
			console.log(this.isPopup);
		}
	}
}
</script>

<style lang="scss">
	.finance-page {
		width: 100%;
		height: 100%;

		display: flex;
		align-items: center;
		justify-content: center;
	}

</style>