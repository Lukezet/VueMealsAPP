<template>
    <div class="p-8">
        <input 
            type="text"
            v-model="keyword" 
            class="rounded border-2 border-gray-500 w-full" 
            placeholder="Search for Meals"
            @change="searchMeals"
        />
    </div>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-3 p-8">
        <div v-for="meal of meals" :key="meal.idMeal" class="bg-white px-6 pt-6 pb-6 rounded-xl shadow-md">
            <img :src="meal.strMealThumb" :alt="meal.strMeal" class="rounded-xl border-4 border-purple-400/25">
            <section class="pt-3">
                <h3 class="p-3 text-lg font-bold">{{ meal.strMeal }}</h3>
                <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Repudiandae laudantium vel culpa ea dicta.</p>
                <div class="my-6">
                    <YouTubeButton :href="meal.strYoutube">Go to YouTube</YouTubeButton>
                    <router-link :to="{name:'mealDetails', params: {id: meal.idMeal}}" class="px-5 py-2 my-3 border-2  border-purple-400 text-purple-500  hover:bg-gradient-to-r from-purple-300 via-purple-400 to-indigo-300  hover:text-white hover:shadow-lg hover:shadow-purple-500/50 hover:border-purple-200 rounded-lg transition-colors">View</router-link>
                </div>
            </section>
        </div>
    </div>
</template>

<script setup>
import { computed } from '@vue/reactivity';
import { onMounted, ref } from 'vue';
import { useRoute } from 'vue-router';
import store from '../store';
import YouTubeButton from "../components/YouTubeButton.vue"


const route = useRoute();
const keyword = ref('');
const meals = computed(()=> store.state.searchedMeals);

function searchMeals(){
    store.dispatch('searchMeals', keyword.value);
}
//Funcion Para mantener el estado al actualizar
onMounted(() => {
    keyword.value = route.params.name
    if (keyword.value){//si hay un texto en el buscador lo mantiene para que si refrescamos la página sigan apareciendo los datos de esa busqueda en pantalla
        searchMeals()
    }
})
</script>