<template>
	<div id="app">
		<h1>Super Quiz</h1>
		<transition name="flip" mode="out-in">
			<Question v-if="questionMode" :question="question[currentQuestion]" @selected="showResult"/>
			<Result v-else :result="result" @confirmed="nextQuestion" />
		</transition>
	</div>
</template>

<script>
import question from '@/util/questions'
import Question from '@/components/Question.vue'
import Result from '@/components/Result.vue'

export default {
	components: {
		Question,
		Result
	},

	data () {
		return {
			result: false,
			questionMode: true,
			question,
			currentQuestion: 0
		}
	},

	methods: {
		showResult (result) {
			this.result = result
			this.questionMode = false
		},

		nextQuestion() {
			let r = Math.random() * (question.length)
			this.currentQuestion = parseInt(r)
			this.questionMode = true
		}
	},
	
	created() {
		this.nextQuestion()
	},


}
</script>

<style>
body {
	background: linear-gradient(45deg , rgb(107, 36, 80), rgb(42, 6, 126), #03012C);
	font-family: 'Alegreya', serif;
	color: #FFF;
	height: 100vh;
}

#app {
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	display: flex;
	flex-direction: column;
	align-items: center;
}

#app h1 {
	font-weight: 200;
	font-size: 4rem;
}

@keyframes flip-out {
	from { transform: rotateY(0deg); }
	to { transform: rotateY(90deg); }
}

@keyframes flip-in {
	from { transform: rotateY(90deg); }
	to { transform: rotateY(0deg); }
}

.flip-enter-active {
	animation: flip-in 0.3s ease;
}

.flip-leave-active {
	animation: flip-out 0.3s ease;
}
</style>
