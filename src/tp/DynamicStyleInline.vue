<template>
    <div id="card2" :style="{ 'background-color': background }" class="card bg-neutral text-neutral-content w-96">
        <div class="card-body items-center text-center">
            <h2 :class="maClass" id="h2" class="card-title">Dynamic Card!</h2>
            <p>We are using [DYNAMIC CARD INLINE] for no reason.</p>
            <div class="card-actions justify-end">
                <label for="color">Choisissez la couleur :</label>
                <textarea v-model="background" placeholder="Secondary" class="textarea textarea-secondary"></textarea>
                <p>Couleur actuelle : <span>{{ background }}</span></p>
                <button @click="RandomizeHexColor()" class="btn btn-primary">Randomize</button>
                <button @click="Reset()" class="btn btn-primary">Reset</button>
                <label for="color">Ecrivez "Hello" ou "World" :</label>
                <textarea @keyup="HelloWorld" v-model="maClass" placeholder="Hello World ?"
                    class="textarea textarea-secondary"></textarea>
                <button @click="Afficherh2" class="btn btn-primary">Afficher < h2> ?</button>
            </div>
        </div>
    </div>
</template>
<script setup lang='js'>
import { ref } from 'vue'
const background = ref("blueviolet");
const maClass = ref("");

function RandomizeHexColor() {
    const letters = '0123456789ABCDEF';
    let color = '#';
    for (let i = 0; i < 6; i++) {
        color += letters[Math.floor(Math.random() * 16)];
    }
    console.log(color);
    return background.value = color;
}
function Reset() {
    return background.value = "blueviolet";
}
function Afficherh2() {
    const h2 = document.querySelector("#h2");
    h2.classList.toggle("hidden");
}
// const HelloWorld = () => {
//     const className = maClass.value;
//     console.log(maClass.value);
//     const h2 = document.querySelector("#h2");
//     if (className === "hello" || className === "Hello") {
//         h2.classList.add("maClasseHello");
//     }
//     if (className === "world" || className === "World") {
//         h2.classList.add("maClasseWorld");
//     }
// }
</script>
<style scoped lang="css">
.card-actions {
    display: flex;
    flex-direction: column;
    align-items: stretch;
}
.hidden {
    display: none;
}
.hello,
.Hello,
.HELLO,
.maClasseHello {
    color: red;
}

.world,
.World,
.WORLD,
.maClasseWorld {
    color: green;
}
</style>