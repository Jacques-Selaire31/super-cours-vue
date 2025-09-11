<template>
  <div class="min-h-screen flex flex-col bg-base-200 text-base-content">
    <!-- Navbar en haut de la page -->
    <AppHeader />
    <!-- Conteneur principal du contenu, centré et responsive -->
    <main class="flex-1 w-full max-w-7xl mx-auto p-4 md:p-8">
      <!-- Ici on aura la router view -->
      <h1>ICI c'est TOULOUSE</h1>
      <router-view></router-view>
      <ButtonNumber></ButtonNumber>
      <InputsEscape></InputsEscape>
      <div id="cards">
        <DynamicStyleClass></DynamicStyleClass>
        <DynamicStyleInline></DynamicStyleInline>
      </div>
      <TpBinding></TpBinding>
    </main>
    <!-- Footer en bas de la page -->
    <AppFooter />
  </div>
</template>

<script setup>
import AppHeader from './components/AppHeader.vue';
import AppFooter from './components/AppFooter.vue';
import ButtonNumber from './tp/ButtonNumber.vue';
import InputsEscape from './tp/InputsEscape.vue';
import TpBinding from './tp/TpBinding.vue';
import DynamicStyleClass from './tp/DynamicStyleClass.vue';
import DynamicStyleInline from './tp/DynamicStyleInline.vue';
// Pas de logique spécifique nécessaire ici,
// Nuxt gère automatiquement la mise en page
// avec les composants de layout.
</script>

<style>
/* Les styles globaux peuvent être ajoutés ici si nécessaire */
/* Par exemple, si vous n'avez pas de fichier main.css séparé */
#cards{
  display: flex;
  flex-direction: row;
  justify-content: center;
  column-gap: 100px;
}
</style>
