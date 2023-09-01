<template>
    <header class="bg-gradient-to-r from-indigo-400 to-purple-500 h-16 flex justify-between items-stretch px-6 shadow-md rounded-bl-3xl rounded-br-3xl">
        <router-link :to="{ name: 'home' }" class="inline-flex items-center h-full text-white transition-colors hover:text-gray-900">
            Home
        </router-link>
        <div flex items-center gap-1>
            <router-link :to="{ name: 'byName' }"
                class="inline-flex items-center px-2 h-full text-white transition-colors  hover:bg-purple-400 hover:hover:text-gray-900">
                Search Meals
            </router-link>
            <router-link :to="{ name: 'byLetter' }"
                class="inline-flex items-center px-2 h-full text-white transition-colors hover:bg-purple-400 hover:hover:text-gray-900">
                Meals by Letter
            </router-link>
            <router-link :to="{ name: 'byIngredient' }"
                class="inline-flex items-center px-2 h-full text-white transition-colors hover:bg-purple-400 hover:hover:text-gray-900">
                Meals by Ingredients
            </router-link>
        </div>
    </header>
</template>

<style>
  .bg-gradient-to-r {
    background-image: linear-gradient(to right, var(--tw-gradient-stops));
  }
</style>