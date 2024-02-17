<script setup>
import { ref,watch } from 'vue';
import q from '../data/quizes.json';
import Card from '../components/Card.vue';

const search = ref('');
const quizes = ref(q);

watch(search, (newVal, oldVal) => {
  if (newVal) {
    quizes.value = q.filter((quiz) =>
      quiz.name.toLowerCase().includes(newVal.toLowerCase())
    );
  } else {
    quizes.value = q;
  }
});

</script>

<template>
  <div>
    <header>
      <h1>Vue Quiz App</h1>
      <input type="text" v-model.trim="search" placeholder="Search" />
    </header>
    <div class="options-container">
      <Card v-for="quiz in quizes" :quiz="quiz" />
    </div>
  </div>
</template>

<style scoped>

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  margin-top: 30px;
}

header h1 {
  font-weight: bold;
  margin-right: 30px;
}

header input {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
  width: 200px;
}
.options-container {
  display: flex;
  flex-wrap: wrap;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 15px;
  margin-top: 20px;
}

</style>