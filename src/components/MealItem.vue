<template>
     <div   
     class="bg-white px-6 pt-6 pb-6 rounded-xl shadow-md"
     >
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
</template>

<script setup>
import YouTubeButton from "../components/YouTubeButton.vue"
const { meal } = defineProps({
    meal:{
        required:true,
        type:Object
    }
})

</script>