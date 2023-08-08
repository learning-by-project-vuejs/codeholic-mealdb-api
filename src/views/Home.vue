<template>
    <div class="p-8 pb-0 text-blue-500">
        <h1 class="text-4xl font-bold mb-4">Random Meals</h1>
    </div>
    <meals :meals="meals" />
</template>

<script setup>
import { onMounted, ref } from 'vue'
import Meals from '../components/Meals.vue'
import axiosClient from '../axiosClient.js'

const meals = ref([])

onMounted(async () => {
    for (let i = 0; i < 12; i++) {
        await axiosClient
            .get(`random.php`)
            .then(({ data }) => meals.value.push(data.meals[0]))
    }
})
</script>