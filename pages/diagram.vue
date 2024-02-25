<template>
	<div class="diagram-page">
		<Diagrams />
	</div>
</template>

<script>
import Diagrams from '~/components/diagram/Diagrams.vue';

export default {
	components: {
		Diagrams,
	},
	setup() {
		
	},
}
</script>

<style lang="scss">
	.diagram-page {
		width: 100%;
		height: 100%;

		display: flex;
		align-items: center;
		justify-content: center;
	}
</style>