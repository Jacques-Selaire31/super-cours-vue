<template>
  <div>
    <NewFriend @add-ami="addAmi"></NewFriend>
    <OnFriend v-for="ami in lesAmis" :id="ami.id" :unAmiName="ami.name" :unAmiPhone="ami.phone" :unAmiMail="ami.email"
      :premium="ami.premium" @delete="DeleteFriendInArray"  @change="ChangePremium"></OnFriend> 
      <span class="alert" v-bind:style="{color:color}">🛑🛑🛑🛑🛑🛑🛑☢️☢️☢️☢️☣️☣️☣️☣️☣️⚠️⚠️⚠️⚠️⚠️⚠️ESPECE DE CON NE MET PAS LES PARENTHESES POUR LES FONCTIONS DANS LE TEMPLATE GROS NOOB!!!!!!!!☢️☢️☢️☢️☣️☣️☣️☣️☣️⚠️⚠️⚠️⚠️⚠️⚠️🛑🛑🛑🛑🛑🛑🛑</span>
</div>
      <!-- <div>
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
      :premium="ami.premium" v-on:click=DeleteFriendInArray  @change="ChangePremium"></OnFriend> 
      <span class="alert" v-bind:style="{color:color}">🛑🛑🛑🛑🛑🛑🛑☢️☢️☢️☢️☣️☣️☣️☣️☣️⚠️⚠️⚠️⚠️⚠️⚠️ESPECE DE CON NE MET PAS LES PARENTHESES POUR LES FONCTIONS DANS LE TEMPLATE GROS NOOB!!!!!!!!☢️☢️☢️☢️☣️☣️☣️☣️☣️⚠️⚠️⚠️⚠️⚠️⚠️🛑🛑🛑🛑🛑🛑🛑</span>
  </div> -->
</template>

<script setup lang='js'>
import { computed, watch, onMounted, onUpdated, onBeforeUnmount, ref } from 'vue'
import OnFriend from './OnFriend.vue';
import NewFriend from './NewFriend.vue';

const color = "red";
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
function addAmi(name, email, phone) {
  const id = crypto.randomUUID();
  lesAmis.value.push({ id : id, name : name, phone : phone, email : email });
}

function ChangePremium(identifiant) {
  let ami = lesAmis.value.find((element) => element.id === identifiant);
  ami.premium = !ami.premium;
}

function DeleteFriendInArray(id) {
  lesAmis.value.splice(id, 1)
}

//
</script>
<style scoped lang="css">
.alert{
    width: 50%;
    border: 4px ridge #f2452c;
    align-items: center;
}
</style>