<template>
  <div>
    <input v-model="text" type="text" placeholder="Type here" class="input" />
    <p>{{ text }}</p>
    <input @keyup.esc="DisplayTextWithEscape()" v-model="textEscapeInput" type="text" placeholder="Type here" class="input" />
    <p>{{ textEscape }}</p>
    <button @click="Alert" class="btn btn-primary">Alerte !</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const text = ref("");
const textEscapeInput = ref("");
const textEscape = ref("");
const alertMessage = "Coucou";

function Alert() {
  alert(alertMessage)
}
function DisplayTextWithEscape(){
    textEscape.value=textEscapeInput.value;
}
</script>