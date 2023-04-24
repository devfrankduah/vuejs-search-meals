<template>
<div class="flex p-8 flex-col justify-center">
    <input type="text" class="rounded border-2 border-gray-200 w-full" placeholder="Search for meals">
    <div class="flex justify-center gap-2 mt-2">
        <router-link v-for="letter of letters" :key="letter" :to="{name: 'byLetter', params: {letter}}" class="px-2 py-1 rounded bg-gray-200 hover:bg-gray-300">
            {{ letter }} 
        </router-link>
    </div>
</div>

</template>
<script setup>
import { computed, onMounted } from "vue";
import store from "../store";
import axiosClient from "../axiosClient";


const meals = computed(() => store.state.meals);
const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split("");

onMounted(async() => {
    const response = await axiosClient.get("/list.php?i=list");
    console.log(response.data);
})
</script>