<template>
    <div class="question-container">
        <h1 class="question">
            {{ question.text }}
        </h1>
    </div>
    <div class="options-container">
        <div v-for="option in question.options" :key="option.id" class="option" @click="emitSelectedOption(option.isCorrect)">
            <p class="option-label">{{ option.label }}</p>
            <div class="option-value">
                <p>{{option.text}}</p>
            </div>
        </div>
    </div>
</template>

<script setup>
import { defineProps,defineEmits } from 'vue';

const emit = defineEmits(["selectOption"])

const {question} = defineProps(["question"])

const emitSelectedOption = (isCorrect) => {
    emit("selectOption",isCorrect)
}

</script>



<style scoped>

.options-container{
    margin-top: 2px;
}

.question{
    font-size: 40px;
    margin-bottom: 20px;
}

.option{
    display: flex;
    margin-bottom: 0px;
    height: 70px;
    cursor: pointer;
}

.option-label{
    background-color: bisque;
    width: 50px;
    height: 50px;
    font-size: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.option-value{
   background-color: rgb(244,239,239);
   width: 100%;
   display: flex;
   flex-direction: row;
   margin-top: 30px;
   padding-left: 10px;
   font-size: 30px;
   height: 50px;
   align-items: center;
}
</style>