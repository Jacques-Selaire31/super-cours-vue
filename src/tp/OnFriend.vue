<template>
  <div>
    <!-- The button to open modal -->
    <h3>{{ unAmiName }}</h3>
    <p v-if="premium === true">AMI PREMIUM 😍</p>
    <p v-else>AMI NUUUUUUUUUUUUUUUL 😒</p>
 <label :for="`modal_${id}`" class="btn">Détails</label>
    <!-- Put this part before </body> tag -->
    <input type="checkbox" class="modal-toggle" :id="`modal_${id}`" />
    <div class="modal" role="dialog">
      <div class="modal-box">
        <h3 class="text-lg font-bold">{{ unAmiName }}!</h3>
        <p class="py-4">{{ unAmiPhone }}</p>
        <p class="py-4">{{ unAmiMail }}</p>
        <div class="modal-action">
           <label :for="`modal_${id}`" class="btn">Close!</label>
        </div>
      </div>
    </div>
    <button @click="ChangePremium()" class="btn btn-success" v-if="premium === false">Ajouter en Premium 😍</button>
    <button @click="ChangePremium()" class="btn btn-success" v-else="premium === true">Ajouter en NUL! 😒</button>
    <button @click="DeleteFriend()" class="btn btn-warning">Supprimer 🥱</button>
  </div>
</template>

<script setup lang='js'>
import { computed, watch, onMounted, onUpdated, onBeforeUnmount, ref } from 'vue'

const props = defineProps({
  id: {
    type: String,
    required: true,
  },
  unAmiName: {
    type: String,
    required: true,
  },
  unAmiPhone: {
    type: String,
    required: true,
  },
  unAmiMail: {
    type: String,
    required: true,
  },
  premium: {
    type: Boolean,
    required: false,
    default: false,
  },
})

const emit = defineEmits(["click"]);
function DeleteFriend() {
  emit("click", props.id);
}
function ChangePremium(){
  props.premium == !props.premium;
}
</script>
<style scoped lang="css"></style>