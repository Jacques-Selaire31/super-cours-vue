<template>
    <div class="flex justify-center my-8">
        <div class="card w-full max-w-xl bg-base-200 shadow-xl p-6">
            <h1 class="text-3xl font-bold text-primary mb-6 text-center">
                Une simple requête HTTP GET
            </h1>

            <!-- Pokémons -->
            <h2 class="text-xl font-semibold text-secondary mb-4">Les Pokémon :</h2>
            <div class="space-y-2">
                <p v-for="(item, index) in pokeArray" :key="index" class="badge badge-primary badge-lg mx-1">
                    {{ item.name }}
                </p>
            </div>

            <div class="divider my-6"></div>

            <!-- Météo -->
            <h2 class="text-xl font-semibold text-secondary mb-4">Météo Toulouse :</h2>
            <div class="grid gap-2">
                <p class="p-2 rounded bg-base-100 shadow-sm">
                    🌡️ Température max : <span class="font-bold">{{ meteo.tmax }}°C</span>
                </p>
                <p class="p-2 rounded bg-base-100 shadow-sm">
                    🌡️ Température min : <span class="font-bold">{{ meteo.tmin }}°C</span>
                </p>
                <p class="p-2 rounded bg-base-100 shadow-sm">
                    🌡️ Température actuelle :
                    <span class="font-bold">{{ meteo.tcurrent }}°C</span>
                </p>
                <p class="p-2 rounded bg-base-100 shadow-sm">
                    ☁️ Condition météo : <span class="font-bold">{{ meteo.condition }}</span>
                </p>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue'

// --- Interfaces ---
interface Pokemon {
    name: string;
    url: string;
}

interface Meteo {
    tmax: number | null;
    tmin: number | null;
    tcurrent: number | null;
    condition: string | null;
}

// --- States ---
const pokeArray = ref < Pokemon[] > ([])
const meteo = ref < Meteo > ({
    tmax: null,
    tmin: null,
    tcurrent: null,
    condition: null,
})

// --- Fonctions de récupération ---
const fetchMeteo = async () => {
    try {
        const response = await fetch('https://prevision-meteo.ch/services/json/toulouse')
        const data = await response.json()
        meteo.value.tmax = data.fcst_day_0.tmax
        meteo.value.tmin = data.fcst_day_0.tmin
        meteo.value.tcurrent = data.current_condition.tmp
        meteo.value.condition = data.current_condition.condition
    } catch (error) {
        console.error('Erreur lors de la récupération de la météo :', error)
    }
}

const fetchPokemon = async () => {
    try {
        const response = await fetch('https://pokeapi.co/api/v2/pokemon/')
        const data = await response.json()
        pokeArray.value = data.results as Pokemon[]
    } catch (error) {
        console.error('Erreur lors de la récupération des Pokémon :', error)
    }
}

// --- Lifecycle ---
onMounted(() => {
    fetchMeteo()
    fetchPokemon()
})

onBeforeUnmount(() => {
    console.log('Le composant va être démonté (changement de page ?)')
})
</script>

<style scoped>
/* Styles custom si besoin */
</style>