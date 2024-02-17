
import QuizHeaderVue from '@/components/QuizHeader.vue';

import QuizHeaderVue from '@/components/QuizHeader.vue';

import QuizHeaderVue from '@/components/QuizHeader.vue';
<script setup>
import Question from '../components/Question.vue';
import QuizHeader from '../components/QuizHeader.vue';
import Result from '../components/Result.vue';

import {ref,watch,computed} from 'vue';
import {useRoute} from 'vue-router';
import quizes from '../data/quizes.json';

const route=useRoute();

const currQuizIndex=ref(0);
const correctAnswer=ref(0);
const quizId= parseInt(route.params.id);
const quiz=quizes.find(q=>q.id===quizId);
const showResults=ref(false)

const questionStasus=computed(()=>`${currQuizIndex.value}/${quiz.questions.length}`);
const barStatus=computed(()=>`${(currQuizIndex.value)/quiz.questions.length*100}%`);

const onSelectedAnswer=(isCorrect)=>{
    if(isCorrect){
        correctAnswer.value++;
    }
    if(quiz.questions.length-1===currQuizIndex.value){
        showResults.value=true;
    }

    currQuizIndex.value++;
}
</script>

<template>
    <div>
        <QuizHeader :questionStasus="questionStasus" :barStatus="barStatus"/>
        <div>
            <Question v-if="!showResults" :question="quiz.questions[currQuizIndex]" @selectOption="onSelectedAnswer"/>
            <Result v-else :quizLength="quiz.questions.length" :correctAnswer="correctAnswer"/>
        </div>
    </div>
</template>

<style scoped>


</style>