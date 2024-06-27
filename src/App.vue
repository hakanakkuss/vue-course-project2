<template>
  <div class="flex justify-around items-center mt-16 gap-4">
    <h1 class="font-bold text-4xl">Quizes App</h1>
    <input v-model="search" type="text" placeholder="Search..." class="border-2 rounded-lg p-2 h-8 bg-gray-100"/>
  </div>

  <div class="flex flex-wrap justify-center mt-10">
    <div v-for="quiz in datas" :key="datas.id" class="hover:shadow-2xl m-4 p-4 bg-slate-50 rounded-lg shadow-xl">
        <img :src="quiz.img" alt="" class="h-40" />
        <h2 class="mt-5 ml-2">{{quiz.name}}</h2>
        <p class="mt-2 ml-2">{{quiz.questions.length}} Questions</p>
    </div>
  </div>


</template>
<script setup>
import q from '@/data/quizDatas.json'
import { ref, watch } from 'vue'

const datas = ref (q)
const search = ref("")

watch(search, () => {
  datas.value = q.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
})

</script>
