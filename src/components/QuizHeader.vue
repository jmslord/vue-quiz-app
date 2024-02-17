<script setup>
import { defineProps } from 'vue';
const { 
        questionStasus, 
        barStatus 
    } = defineProps([
        'questionStasus', 
        'barStatus'
        ])

</script>
<template>
    <header>
        <h4>Question {{ questionStasus }}</h4>
        <div class="bar">
            <div class="completion" :style="{width:barStatus}"></div>
        </div>
    </header>
</template>

<style scoped>
header {
    margin-top: 30px;
}

header h4 {
    font-weight: bold;
    font-size: 30px;
    margin-bottom: 20px;
}

.bar {
    width: 100%;
    height: 20px;
    background-color: #ddd;
    border-radius: 10px;
    position: relative;
}

.completion {
    width: 0%;
    height: 100%;
    background-color: #4caf50;
    border-radius: 10px;
}
</style>