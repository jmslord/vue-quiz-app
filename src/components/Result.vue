<script setup>
import { defineProps } from 'vue';
import {RouterLink} from 'vue-router';

const { quizLength, correctAnswer } = defineProps(['quizLength', 'correctAnswer'])
</script>
<template>
    <div class="results">
        <p>Your Results...</p>
        <h1>{{correctAnswer}}/{{ quizLength }}</h1>
        <RouterLink to="/" class="btn">Go Back</RouterLink>
    </div>
</template>

<style scoped>
.results {
    margin-top: 20px;
    text-align: center;
    font-size: 30px;
    font-weight: bold;
    padding: 100px 0;
}

p {
    font-size: 25px;
}

h1 {
    margin-top: 20px;
    font-size: 80px;
}
</style>