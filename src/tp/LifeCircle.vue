<template>
  <div>
    <input v-model="value" />
    <h3 id="title_meteo">Condition météo à Toulouse : </h3>
    <p>Date : {{ arrayMeteo[0] }}</p>
    <p>Condition actuelle : {{ arrayMeteo[1] }}</p>
    <p>Température actuelle : {{ arrayMeteo[4] }}</p>
    <p>Température minimale du jour : {{ arrayMeteo[2] }}</p>
    <p>Température maximale du jour : {{ arrayMeteo[3] }}</p>
  </div>
  <div>
    <h3>Nos supers POKEMON</h3>
    <p class="badge badge-primary" v-for="poke, index  in arrayPokemon" :key="index"> {{ poke }}</p>
  </div>
</template>

<script setup lang='js'>
import { computed, watch, onMounted, onUpdated, onBeforeUnmount, onBeforeMount, ref } from 'vue'

const arrayMeteo = ref([]);
const arrayPokemon = ref([]);

const FetchAPIMeteo = async () => {
  try {
    const rawData = await fetch('https://prevision-meteo.ch/services/json/toulouse');
    console.log(rawData);

    // Vérification du statut de la réponse
    if (!rawData.ok || rawData.status !== 200) { // Vérification du statut 200
      console.error("Erreur lors de la récupération des données : ", rawData.statusText);
      return; // Sortir de la fonction si la réponse n'est pas OK
    }
    const transformedData = await rawData.json();
    console.log(transformedData);
    const jour = transformedData.current_condition.date;
    const condition = transformedData.fcst_day_0.condition;
    const tmin = transformedData.fcst_day_0.tmin;
    const tmax = transformedData.fcst_day_0.tmax;
    const tmp = transformedData.current_condition.tmp;
    arrayMeteo.value.push(jour);
    arrayMeteo.value.push(condition);
    arrayMeteo.value.push(tmin);
    arrayMeteo.value.push(tmax);
    arrayMeteo.value.push(tmp);
  } catch (error) {
    console.error("Erreur lors de l'appel à l'API : ", error);
  }
}

const FetchAPIPokemon = async () => {
  try {
    const rawData = await fetch('https://pokeapi.co/api/v2/pokemon/?offset=20&limit=20');
    // Vérification du statut de la réponse
    if (!rawData.ok || rawData.status !== 200) { // Vérification du statut 200
      console.error("Erreur lors de la récupération des données : ", rawData.statusText);
      return; // Sortir de la fonction si la réponse n'est pas OK
    }
    const transformedData = await rawData.json();
    console.log(transformedData);
    for (let i = 0; i < transformedData.results.length; i++) {
      arrayPokemon.value.push(transformedData.results[i].name);
    }
    console.log(arrayPokemon);
  } catch (error) {
    console.error("Erreur lors de l'appel à l'API : ", error);
  }
}

const props = defineProps({
  // v-model
  modelValue: {
    default: '',
  },
});

const emit = defineEmits({
  // v-model event with validation
  'update:modelValue': (value) => value !== null,
});

const value = computed({
  get() {
    return props.modelValue;
  },
  set(value) {
    emit('update:modelValue', value);
  },
});

const stopWatch = watch(
  () => props.modelValue, async (_newValue, _oldValue) => {
    // do something
  },
  {
    immediate: true
  }
);
onBeforeMount(() => {

})

onMounted(() => {
  FetchAPIMeteo();
  FetchAPIPokemon();
});

onUpdated(() => {
});

onBeforeUnmount(() => {
  stopWatch();
});

</script>

<style scoped lang="css"></style>