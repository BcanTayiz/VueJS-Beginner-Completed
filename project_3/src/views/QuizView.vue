<template>
    <div>
        <QUizHeader :questionStatus="questionStatus" :barPercentage="barPercentage"/>
        <div>
            <Question v-if="!showResults"
             :question="quiz.questions[currentQuestionIndex]" @selectOption="onOptionSelected"/>
             <Result v-else :quizQuestionLenght="quiz.questions.length" :numberOfCorrectAnswers="numberOfCorrectAnswers"/>
        </div>
        
    </div>
</template>

<script setup>
import Question from '../components/Question.vue'
import QUizHeader from '../components/QuizHeader.vue'
import { useRoute } from "vue-router"
import { ref,computed } from 'vue';
import quizes from '../data/quizes.json'
import Result from '../components/Result.vue'

const route = useRoute()
const quizId = parseInt(route.params.id)
const currentQuestionIndex = ref(0)
const quiz = quizes.find(q => q.id == quizId)
const numberOfCorrectAnswers = ref(0)
const showResults = ref(false)

/* const questionStatus = ref(`${currentQuestionIndex.value}/${quiz.questions.length}`)

watch(() => currentQuestionIndex.value, () => {
    questionStatus.value = `${currentQuestionIndex.value}/${quiz.questions.length}`
}) */

const questionStatus = computed(() => {
    return `${currentQuestionIndex.value}/${quiz.questions.length}`
})
const barPercentage = computed(() => {
    return `${(currentQuestionIndex.value / quiz.questions.length) * 100 }%`
})

const onOptionSelected = (isCorrect) => {
    if(isCorrect){
        numberOfCorrectAnswers.value++
    }

    if(quiz.questions.length - 1=== currentQuestionIndex.value){
        showResults.value = true
    }
    currentQuestionIndex.value++
}
</script>


<style scoped>
button{
    margin-top: 50px;
}
</style>