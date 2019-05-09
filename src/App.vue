<template>
	<div class="container">
		<div class="row">
			<div class="col-lg-12 col-xs-12">
				<h1 class="text-center">Math Quiz</h1>
			</div>
		</div>
		<hr>
		<br>
		<div class="row">
			<div class="col-md-6 col-xs-6 offset-md-3 offset-xs-6">
				<div class="card">
					<transition name="flip" mode="out-in">
						<component
							class="animated flipInY"
							:is="currentCard"
							:content="question"
							@answerChosen="determineResult"
							@next="nextQuestion"/>
					</transition>
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
			question: this.determineQuestionParts(),
			mode: 0
		}
	},
	computed: {
		currentCard() {
			return this.mode ? 'answer' : 'question'
		}
	},
	methods: {
		shuffle(array) {
			let currentIndex = array.length
			let randomIndex, temp
			while (currentIndex !== 0) {
				randomIndex = Math.floor(Math.random() * currentIndex)
				currentIndex--

				temp = array[currentIndex]
				array[currentIndex] = array[randomIndex]
				array[randomIndex] = temp
			}
			return array
		},
		randomNumberBetween(min,max) {
			return Math.floor(Math.random() * (max - min + 1) + min)
		},
		determineOptions(answer, operation) {
			let littleBigger = answer + this.randomNumberBetween(1, 3)
			let littleSmaller = answer - this.randomNumberBetween(1, 3)
			const someNum = this.randomNumberBetween(3, 25)
			let wayOff = operation ? answer + someNum : answer - someNum
			let options = [answer, littleBigger, littleSmaller, wayOff]
			options = this.shuffle(options)
			return options
		},
		determineQuestionParts() {
			const a = this.randomNumberBetween(1,999)
			const b = this.randomNumberBetween(1,999)
			const operation = Math.floor(Math.random() * 2)
			const answer = operation ? a + b : a - b
			const options = this.determineOptions(answer, operation)
			return {
				question: `What is ${a} ${ operation ? '+' : '-' } ${b}?`,
				options,
				answer
			}
		},
		determineResult(event) {
			const answer = this.question.options[event]
			if (answer === this.question.answer) {
				this.mode = 1
			} else {
				alert('Wrong answer! \n\n Try again.')
			}
		},
		nextQuestion() {
			this.question = this.determineQuestionParts()
			this.mode = 0
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
		border-radius: 8px !important;
	}
</style>

<style scoped>
.flip-enter {

}
.flip-enter-active {

}
.flip-leave {

}
.flip-leave-active {

}
</style>
