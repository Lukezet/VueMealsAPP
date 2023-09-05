<template>
    <div>
        <router-link 
            :to="{
            name: 'byIngredient', 
            params:{ ingredient: ingredient.idIngredient }
            }" 
            v-for="ingredient of ingredients" 
            :key="ingredient.idIngredient" 
            class="block bg-white shadow-md mx-12 my-6 p-6 mb-3 rounded-xl border-4 border-purple-400/25"
            >
            <pre>{{ ingredient.idIngredient }}</pre>
            <h3 class="txt-2xl font-bold">{{ingredient.strIngredient}}</h3>
            <p>{{ ingredient.strDescription }}</p>
        </router-link>
    </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import axiosClient from '../axiosClient';


const ingredients = ref([]);

onMounted(() => {
    axiosClient.get("list.php?i=list")
        .then(({data})=>{
            ingredients.value = data.meals;
        });
});

</script>