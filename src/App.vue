<script setup>
import MyMovies from './components/MyMovies.vue';
import { useMovieStore } from './stores/movieStore';

const movieStore = useMovieStore();

// Функция для изменения activeTab
const setActiveTab = (tab) => {
  movieStore.activeTab = tab;
};

console.log(movieStore);
</script>

<template>
  <header class="header flex gap-4 items-center justify-center pt-[20px] pb-[40px] flex-col">  
    <div class="img-wrapp w-[100px]">
      <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQx3_s-ZvlY-S_i8mB7gQCuNepszOi0nLrrdg&s" alt="">
    </div>
    <h2 class="text-3xl font-bold">My Favorite movies</h2>

    <nav class="flex gap-4 items-center">
      <!-- Кнопка для переключения на вкладку "Movies" -->
      <button 
        :class="{ 'btn-green': movieStore.activeTab === 1 }"
        @click="setActiveTab(1)"
      >
        Movies
      </button>
      <!-- Кнопка для переключения на вкладку "Search" -->
      <button 
        :class="{ 'btn-green': movieStore.activeTab === 2 }"
        @click="setActiveTab(2)"
      >
        Search
      </button>
    </nav>
  </header>
  <main>
    <!-- Секция "Movies" -->
    <div class="all-movies w-[700px] mx-auto flex flex-col gap-6 pb-10" v-if="movieStore.activeTab === 1">
      <h2 class="text-2xl font-bold">All movies</h2>
      <MyMovies v-for="movie in movieStore.movies" :key="movie.id" :movie="movie" />
    </div>

    <!-- Секция "Search" -->
    <div class="search w-[700px] mx-auto flex flex-col gap-6 pb-10" v-else>
      <h2 class="text-2xl font-bold">Search movies</h2>
    </div>
  </main>
  <footer>
  </footer>
</template>
<style scoped>
.elem {
  will-change: filter;
  transition: filter 300ms linear;
}
.h-elem:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
  transition: .3s ease-in-out;
}
button {
  border-radius: 8px;
  padding: 0.6em 1.2em;
  font-size: 1em;
  font-weight: 500;
  font-family: inherit;
  cursor: pointer;
  transition: border-color 0.25s;
  color: black;
}
button:hover {
  scale: 1.1;
  transition: .3s ease-in-out
}
button:focus,
button:focus-visible {
  outline: 4px auto rgba(0, 0, 0, 0.5);
}
.btn-green{
  background-color: #42b883aa;
}
</style>
