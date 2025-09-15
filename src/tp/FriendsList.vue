<template>
  <div>
    <input v-model="value" />
    <div>
      <label for="name">Nom:</label>
      <input v-model="name" type="text" placeholder="Votre nom" class="input input-secondary" />
    </div>
    <div> <label for="phone">Téléphone:</label>
      <input v-model="phone" type="number" placeholder="Votre téléphone" class="input input-secondary" min="10" max="10" />
    </div>
    <div> <label for="email">Email:</label>
      <input v-model="email" type="email" placeholder="Votre email" class="input input-secondary" />
    </div>
    <button class="btn btn-secondary">Ajouter ami</button>
    <OnFriend>
    </OnFriend>
  </div>
</template>

<script setup lang='js'>
import { computed, watch, onMounted, onUpdated, onBeforeUnmount, ref } from 'vue'
import OnFriend from './OnFriend.vue';

const name = ref("");
const phone = ref("");
const email = ref("");
// const html = <div v-html="OnFriend"></div> 

const AddFriend = ()=>{
    const ami = {name : name, phone : phone, email :email, premium : false}
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
  get () {
    return props.modelValue;
  },
  set (value) {
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

onMounted(() => {
});

onUpdated(() => {
});

onBeforeUnmount(() => {
  stopWatch();
});

</script>

<style scoped lang="css">
</style>