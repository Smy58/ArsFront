<template>
	<div class="layout">
		<TheNavigation />
		<slot />
	</div>
</template>

<script lang="ts">
import TheNavigation from '../components/TheNavigation.vue'
import '../assets/fonts/Gilroy/stylesheet.css'

export default {
	components: {
		TheNavigation

	}
}
</script>

<style lang="scss">
	body {
		margin: 0;
		padding: 0;

		
	}

	#__nuxt {
		width: 100%;
	}
 
	.layout {
		width: 100%;
		display: flex;
		align-items: center;
		justify-content: center;

		flex-direction: column;
		padding-top: 86px;
	}
</style>