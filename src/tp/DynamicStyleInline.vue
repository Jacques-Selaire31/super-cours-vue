<template>
    <div @click=" background = 'blueviolet'" id="card2" :style="{'background-color': background}" class="card bg-neutral text-neutral-content w-96">
        <div class="card-body items-center text-center">
            <h2 class="card-title">Dynamic Card!</h2>
            <p>We are using [DYNAMIC CARD INLINE] for no reason.</p>
            <div class="card-actions justify-end">
                <textarea v-model="background" placeholder="Secondary" class="textarea textarea-secondary"></textarea>
            </div>
        </div>
    </div>
</template>
<script setup lang='js'>
import { ref } from 'vue'
const background = ref("blueviolet");
</script>
<style scoped lang="css"></style>