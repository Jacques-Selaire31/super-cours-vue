<template>
    <div id="film">
        <label for="film">Entrez le nom d'un film</label>
        <textarea v-model="movieName" name="movie-area" id="movie-area" placeholder="Nom du film..."></textarea>
        <button @click="addMovie" class="btn btn-primary">Ajouter le film</button>
        <span @click="deleteMovie" v-if="arrayMovie.length" v-for="movie, index in arrayMovie" :id="index"> {{ index+1 }} {{ movie }}
        </span>
        <span v-else>Veuillez rentrer un film dans la liste</span>
    </div>
</template>
<script setup lang='js'>
import { ref } from 'vue';
const arrayMovie = ref([]);
const movieName = ref("");
const addMovie = () => {
    arrayMovie.value.push(movieName.value);
    movieName.value = "";
}
const deleteMovie = (index) => {
    arrayMovie.value.splice(index,1)
}
</script>
<style scoped lang="css">
#film {
    display: flex;
    flex-direction: column;
    row-gap: 20px;
    width: 50%;
    align-items: center;
    justify-content: center;
}

.hidden {
    display: none;
}
</style>