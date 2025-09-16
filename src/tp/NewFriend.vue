<template>
  <div>
    <div>
      <label for="name">Nom:</label>
      <input v-model="name" type="text" placeholder="Votre nom" class="input input-secondary" />
    </div>
    <div> <label for="phone">Téléphone:</label>
      <input v-model="phone" type="number" placeholder="Votre téléphone" class="input input-secondary" min="10"
        max="10" />
    </div>
    <div> <label for="email">Email:</label>
      <input v-model="email" type="email" placeholder="Votre email" class="input input-secondary" />
    </div>
    <button @click="giveAmiToParent" class="btn btn-secondary">Ajouter ami</button>
  </div>
</template>

<script setup lang='js'>
import { computed, watch, onMounted, onUpdated, onBeforeUnmount, ref } from 'vue'

const name = ref("");
const phone = ref("");
const email = ref("");
const props = defineProps({
  
  // v-model
  modelValue: {
    default: '',
  },
});

const emit = defineEmits(["add-ami"]);

function giveAmiToParent(){
  emit("add-ami",{ name :name.value, phone : phone.value, email : email.value})
}

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