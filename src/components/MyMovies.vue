<template>
    <section class="move rounded-xl p-4 bg-gray-50 cursor-pointer h-elem flex gap-[50px]">
      <div class="movie-logo flex justify-center w-[300px] mx-auto">
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQx3_s-ZvlY-S_i8mB7gQCuNepszOi0nLrrdg&s" alt="">
      </div>
      <div class="movie-text flex flex-col gap-4">
        <div class="movie-name flex justify-between">
          <span class="font-bold">{{ movie.original_title }}</span>
          <span class="text-sm text-gray-400 pb-4">{{ movie.release_date }}</span>
        </div>
        <p class="text-gray-500">{{ movie.overview }}</p>
        <div class="btn-group flex gap-4 items-center justify-end">
          <button class="bg-green-200">Watched</button>
          <button class="bg-red-200">Delete</button>
        </div>
      </div>
    </section>
  </template>
    
  <script setup>

  const props = defineProps({
    movie: {
      type: Object,
      required: true, 
    },
  });
  </script>
<style scoped>
.movie-logo img {
  width: 100%;
  height: 100%;
  object-fit: contain;
}
.movie-text {
  height: fit-content;
  margin: auto;
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

</style>