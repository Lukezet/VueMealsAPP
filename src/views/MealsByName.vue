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
    <Meals :meals="meals"/>
</template>

<script setup>
import { computed } from '@vue/reactivity';
import { onMounted, ref } from 'vue';
import { useRoute } from 'vue-router';
import store from '../store';
import Meals from "../components/Meals.vue"



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