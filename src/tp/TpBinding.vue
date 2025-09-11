<template>
    <!-- Open the modal using ID.showModal() method -->
    <button id="btn" class="btn" onclick="my_modal_1.showModal()">{{name}}</button>
    <dialog id="my_modal_1" class="modal">
        <div class="modal-box">
            <div class="card bg-base-100 w-96 shadow-sm">
                <figure>
                    <img :src=srcIMG alt="Shoes" />
                </figure>
                <div class="card-body">
                    <h2 class="card-title">{{ name }}</h2>
                    <p>Age : {{ age }}</p>
                    <input type="text" :value="name">
                    <p>Age +10 : {{ CaulculAGE(age) }}</p>
                    <p>Son nombre favori : {{ RandomNum() }}</p>
                    <div v-html="html"></div>
                    <div class="card-actions justify-end">
                    </div>
                </div>
            </div>
            <div class="modal-action">
                <form method="dialog">
                    <!-- if there is a button in form, it will close the modal -->
                    <button class="btn">Close</button>
                </form>
            </div>
        </div>
    </dialog>
</template>

<script setup>
// Pas de logique spécifique pour un composant de footer.
import { ref } from 'vue'
const srcIMG = ref("https://picsum.photos/200/300");
const name = ref("DARK MARIO");
const age = ref(666);
const html = "<p> HE CON JE SUIS DU HTML GENERE PAR v-html</p>"
function CaulculAGE(age) {
    return age + 10;
}
function RandomNum() {
    return Math.random();
}

</script>

<style scoped>
#btn {
    height: 75px;
    width: 75px;
}
</style>
