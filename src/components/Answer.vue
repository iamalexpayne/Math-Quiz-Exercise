<template>
	<div class="success text-center">
		<div class="card-body">
			<h1>That's Correct!</h1>
		</div>
		<div class="card-footer">
			<button class="btn btn-primary">Next Question</button>
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
	h1 {
		margin: 8px auto;
		font-weight: bold;
		color: green;
	}
	.success {
		background-color: lightgreen;
	}
</style>
