<template>
	<div class="card">
		<div class="card-body">
			<h1>That's Correct!</h1>
		</div>
		<div class="card-footer text-center">
			<button class="btn btn-primary" @click="next">Next Question</button>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		content: Object
	},
	methods: {
		next() {
			this.$emit('next')
		}
	}
}
</script>

<style scoped>
	h1 {
		margin: 64px auto;
		font-weight: bold;
		color: green;
	}
	.card {
		background-color: lightgreen;
		text-align: center;
		min-height: 267px;
	}
</style>
