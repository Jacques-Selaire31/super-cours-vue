<template>
  <div>
    <input v-model="value" />
    <div>
      <label for="id">id:</label>
      <input v-model="id" type="text" placeholder="Votre id" class="input input-secondary" />
    </div>
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
    <button v-on:click="addFriend(id,name, phone, email)" class="btn btn-secondary">Ajouter ami</button>
    <OnFriend v-for="ami in lesAmis" :id="ami.id" :unAmiName="ami.name" :unAmiPhone="ami.phone" :unAmiMail="ami.email"
      :premium="ami.premium" v-on:click=DeleteFriendInArray></OnFriend>
  </div>
</template>

<script setup lang='js'>
import { computed, watch, onMounted, onUpdated, onBeforeUnmount, ref } from 'vue'
import OnFriend from './OnFriend.vue';

const id = ref("");
const name = ref("");
const phone = ref("");
const email = ref("");
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
    name: 'COCO L ASTICOT NUL !',
    phone: '0123456789',
    email: 'coco@lasticot.com',
    premium: false
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

function DeleteFriendInArray(id) {
  lesAmis.value.splice(id, 1)
}
function addFriend(id,name, phone, email){
lesAmis.value.push({id,name, phone, email});
}
</script>
