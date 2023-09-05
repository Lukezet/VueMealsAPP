<template>
<div class="justify-center flex gap-1 mt-2">
    <router-link :to="{name: 'byLetter', params:{letter}}" v-for="letter of letters" :key="letter">
        {{ letter }}        
    </router-link>    
</div>
<div class="grid grid-cols-1 md:grid-cols-3 gap-3 p-8">
    <MealItem v-for="meal of meals" :key="meal.idMeal" :meal="meal"/>
</div>
</template>

<script setup>
import { computed } from '@vue/reactivity';
import store from '../store';
import { onMounted,watch } from 'vue';
import { useRoute } from 'vue-router';
import MealItem from '../components/MealItem.vue';

const route = useRoute();
const letters = 'ABCDFGHIJKLMNOPQRSTUVWXYZ'.split("");
const meals = computed(() => store.state.mealsByLetter);

watch(route,()=>{
    store.dispatch('searchMealsByLetter', route.params.letter);
})

onMounted(() => {
    store.dispatch('searchMealsByLetter', route.params.letter);

})

</script>
