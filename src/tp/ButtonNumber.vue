<template>
    <div>
        <button @click.right="count = count - decr" class="btn btn-error">-</button>
        <p>le nombre : {{ count }}</p>
        <p>{{ DisplayUserName }}</p>
        <button @click.middle="count = count + incr" class="btn btn-success">+</button>
    </div>
</template>
<script setup lang='js'>
import { ref, computed, watch} from 'vue'
let count = ref(0);
const decr = ref(1);
const incr = ref(1);
const username = ref();
const DisplayUserName = computed(() => {
    console.log("okok la fonction marche");
    if (username == "") {
        return "okok elle est vide";
    } else "pas okok elle est pas vide";
});
watch(count,(newCount) => {
    if (newCount == 7) {
        count.value = 0;
    }
});
</script>
<style scoped lang="css"></style>



<!------------------------------VERSION BUG----------------------------------------------------

<template>
    <div>
        <button @click.right="count = count - decr" class="btn btn-error">-</button>
        <p>le nombre : {{ count }}</p>
        <p>{{ DisplayUserName() }}</p>
        <button @click.middle="count = count + incr" class="btn btn-success">+</button>
    </div>
</template>
<script setup lang='js'>
import { ref } from 'vue'
let count = ref(0);
const decr = ref(11);
const incr = ref(5);
const username = ref();
function DisplayUserName(){
    console.log("okok la fonction marche");
    if (username ==""){
        return "okok elle est vide";
    } else "pas okok elle est pas vide";
}
</script>
<style scoped lang="css"></style> -->
