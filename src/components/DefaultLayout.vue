<template>
    <div class="bg-white h-full">
        <NavBar />
        <main>
            <router-view />
        </main>
    </div>
</template>

<script setup>
import NavBar from '../components/NavBar.vue'
</script>
