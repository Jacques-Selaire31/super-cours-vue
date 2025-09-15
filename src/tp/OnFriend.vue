<template>
  <div v-for="ami in lesAmis">
    <!-- The button to open modal -->
    <h3>{{ ami.name }}</h3>
    <p v-if="premium === true">AMI PREMIUM 😍</p>
    <p v-else>AMI NUUUUUUUUUUUUUUUL 😒</p>
    <label for="my_modal_6" class="btn">Détails</label>
    <!-- Put this part before </body> tag -->
    <input type="checkbox" class="modal-toggle" id="my_modal_6" />
    <div class="modal" role="dialog">
      <div class="modal-box">
        <h3 class="text-lg font-bold">{{ ami.name }}!</h3>
        <p class="py-4">{{ ami.phone }}</p>
        <p class="py-4">{{ ami.email }}</p>
        <div class="modal-action">
          <label for="my_modal_6" class="btn">Close!</label>
        </div>
      </div>
    </div>
    <button class="btn btn-success">Ajouter en Premium 😍</button>
    <button class="btn btn-warning">Supprimer 🥱</button>
  </div>
</template>

<script setup lang='js'>
import { computed, watch, onMounted, onUpdated, onBeforeUnmount, ref } from 'vue'

const props = defineProps({
  id: Number,
  name: String,
  phone: Number,
  email: String,
  premium: Boolean
});
const lesAmis = ref([
  {
    id: 'lasticot',
    name: 'COCO L ASTICOT',
    phone: '0123456789',
    email: 'coco@lasticot.com',
    premium: true
  },
  {
    id: 'lasticot2',
    name: 'COCO L ASTICOT',
    phone: '0123456789',
    email: 'coco@lasticot.com',
    premium: true
  },
  {
    id: 'kimonoSurUnFrigo',
    name: "Steven Seagal",
    phone: '3387654770',
    email: 'steven@seagal.com',
    premium: true
  },
  {
    id: 'yoyoyo',
    name: "JAROD",
    phone: '3876005477',
    email: 'jAROD@seagal.com',
    premium: true
  }
]);


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

onMounted(() => {
});

onUpdated(() => {
});

onBeforeUnmount(() => {
  stopWatch();
});

</script>

<style scoped lang="css"></style>