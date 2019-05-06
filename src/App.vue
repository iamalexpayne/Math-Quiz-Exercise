<template>
	<div class="container">
		<div class="row">
			<div class="col-lg-12 col-xs-12">
				<h1 class="text-center">Math Quiz</h1>
			</div>
		</div>
		<hr>
		<div class="row">
			<div class="col-md-6 col-xs-6 offset-md-3 offset-xs-6">
				<div class="card">

						<question :content="question"></question>
						<answer></answer>

				</div>
			</div>
		</div>
	</div>
</template>

<script>
import Question from './components/Question.vue'
import Answer from './components/Answer.vue'

export default {
	components: {
		Question,
		Answer
	},
	data() {
		return {
			question: {
				question: 'What is x + y?',
				options: [1,23,52,63]
			}
		}
	}
}
</script>

<style>
	* {
		font-family: sans-serif;
	}

	h1 {
		margin: 48px auto;
	}

	.card {
		box-shadow: 0 4px 8px lightgray;
		border-radius: 8px;
	}
</style>
