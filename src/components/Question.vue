<script setup>
import { defineProps, defineEmits } from 'vue';
const {question}=defineProps(['question'])
const emit=defineEmits(['selectOption'])

const emitSelectedOption=(isCorrect)=>{
    emit('selectOption',isCorrect)
}

</script>

<template>
    <div class="question-container">
        <h1 class="question">{{ question.text }}</h1>
        <div class="options-container">
            <div :key="option.id" v-for="option in question.options" class="option" @click="emitSelectedOption(option.isCorrect)">
                <p class="option-label">{{ option.label }}</p>
                <div class="option-value">{{ option.text }}</div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.question-container {
    margin-top: 20px;
}

.question{
    font-size: 40px;
    font-weight: bold;
    margin-bottom: 20px;
}

.option{
    display: flex;
    align-items: center;
    margin-bottom: 20px;
    cursor: pointer;
}

.option-label{
    background-color: rgb(230, 40, 40);
    padding: 10px;
    width:50px;
    margin-left: 15px;
    font-size: 20px;
    font-weight: bold;
    display:flex;
    align-items: center;
    justify-content: center;
}

.option-value{
    background-color: rgb(216, 115, 115);
    margin-left: 10px;
    font-size: 20px;
    font-weight: bold;
    width: 100%;
    padding: 10px;
}
</style>