<script setup>
import { defineProps } from 'vue';
import {useRouter} from 'vue-router';

const router=useRouter();

const {quiz}=defineProps(['quiz'])


const goToQuiz=()=>{
    router.push(`/quiz/${quiz.id}`)
}

</script>

<template>
    <div class="card" @click="goToQuiz">
        <img :src="quiz.img" alt="Quiz" />
        <div class="card-text">
          <h2>{{ quiz.name }}</h2>
          <p>{{ quiz.questions.length}} Questions</p>
        </div>
      </div>
</template>

<style scoped>
/* Card */
.card {
  /* background-color: #fff; */
  width: 310px;
  margin-bottom: 35px;
  margin-bottom: 20px;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
  border-radius: 5px;
  overflow: hidden;
  cursor: pointer;
}
.card img {
  width: 100%;
  object-fit: cover;
}

.card-text {
  padding: 0 5px;
}

.card .card-text h2 {
  font-size: 1.5rem;
  font-weight: bold;
  margin: 10px 0;
}
</style>