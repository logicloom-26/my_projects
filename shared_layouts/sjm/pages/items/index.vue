<script setup>
const movies = [
  { id: 1, title: 'Inception', year: 2010, genre: 'Science Fiction' },
  { id: 2, title: 'The Dark Knight', year: 2008, genre: 'Action' },
  { id: 3, title: 'Interstellar', year: 2014, genre: 'Science Fiction' },
  { id: 4, title: 'Avengers: Endgame', year: 2019, genre: 'Superhero' },
  { id: 5, title: 'The Matrix', year: 1999, genre: 'Science Fiction' }
]
</script>
<template>
  <section>
    <h2 class="page-title">Movie List</h2>
    <div
      v-for="movie in movies"
      :key="movie.id"
      class="movie"
    >
      <h3>{{ movie.title }}</h3>
      <p><strong>Year:</strong> {{ movie.year }}</p>
      <p><strong>Genre:</strong> {{ movie.genre }}</p>
      <NuxtLink class="button" :to="`/items/${movie.id}`">
        View Details
      </NuxtLink>
    </div>
  </section>
</template>