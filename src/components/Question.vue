<template>
	<div>
		<div class="card-header">
			<h4>{{ content.question }}</h4>
		</div>
		<div class="card-body">
			<div class="row">
				<div class="col-sm-6 text-center" v-for="option in content.options">
					<button class="btn btn-primary">{{ option }}</button>
				</div>
			</div>
		</div>

	</div>
</template>

<script>
export default {
	props: {
		content: Object
	}
}
</script>

<style scoped>
	h4 {
		margin: 0 auto;
		text-align: center;
	}

	button {
		margin: 24px auto;
		min-width: 64px;
	}
</style>
