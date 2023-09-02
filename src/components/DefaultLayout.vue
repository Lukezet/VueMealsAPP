<template>
    <div class="bg-stone-200 h-full">
        <NavBar />
        <main>
            <router-view />
        </main>
    </div>
</template>

<script setup>
import NavBar from '../components/NavBar.vue'
</script>
