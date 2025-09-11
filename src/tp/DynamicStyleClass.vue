<template>
<div id="card" @click="DynamicStyle" class="card bg-neutral text-neutral-content w-96">
  <div class="card-body items-center text-center">
    <h2 class="card-title">Dynamic Card!</h2>
    <p>We are using [DYNAMIC CARD BY CLASS] for no reason.</p>
    <div class="card-actions justify-end">
      <button class="btn btn-primary">Accept</button>
      <button class="btn btn-ghost">Deny</button>
    </div>
  </div>
</div>
</template>
<script setup lang='js'>
const DynamicStyle = ()=>{
  const card = document.getElementById("card");
  card.classList.toggle("dynamic");
}
</script>
<style scoped lang="css">
.dynamic{
  background-color: blueviolet;
  color: white;
  outline: rgba(255,255,255,.6) solid 4px;
  outline-offset: .2em;
  border-radius: .2em;
}
</style>