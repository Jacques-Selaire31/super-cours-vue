<template>
  <div class="chat chat-start">
    <div class="chat-image avatar">
      <div class="w-10 rounded-full">
        <img alt="Tailwind CSS chat bubble component"
          src="https://img.daisyui.com/images/profile/demo/kenobee@192.webp" />
      </div>
    </div>
    <div class="chat-bubble">It was said that you would, destroy the Sith, not join them.</div>
    <p>{{ string }}</p>
    <p>{{ tab }}</p>
    <p>{{ returnSomething() }}</p>
    <p>{{ random() }}</p>
  </div>
  <div class="chat chat-start">
    <div class="chat-image avatar">
      <div class="w-10 rounded-full">
        <img alt="Tailwind CSS chat bubble component"
          src="https://img.daisyui.com/images/profile/demo/kenobee@192.webp" />
      </div>
    </div>
    <div class="chat-bubble">It was you who would bring balance to the Force</div>
  </div>
  <div class="chat chat-start">
    <div class="chat-image avatar">
      <div class="w-10 rounded-full">
        <img alt="Tailwind CSS chat bubble component"
          src="https://img.daisyui.com/images/profile/demo/kenobee@192.webp" />
      </div>
    </div>
    <div class="chat-bubble">Not leave it in Darkness</div>
  </div>
</template>

<script setup lang="js">
const string = "Bonjour, je suis une string";
const tab = [{ title: "Je suis un objet", content: "et voici mon contenu" }, { title: "Héhé on est dans un tableau", content: "Hé oui con" }]
function returnSomething() {
  return "Eh cooooon je suis une fonction qui retourne"
}
function random() {
  let count = Math.random();
  console.log(count);
  return count > 0.5 ?  "Le livre de Bobba Fett" : "Le livre dela JUNGLE";
}
</script>
<style scoped></style>