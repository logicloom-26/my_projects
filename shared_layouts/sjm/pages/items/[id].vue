<script setup>
const movies = [
  {
    id: 1,
    title: 'Inception',
    year: 2010,
    genre: 'Science Fiction',
    description: 'A thief enters people’s dreams to steal information.'
  },
  {
    id: 2,
    title: 'The Dark Knight',
    year: 2008,
    genre: 'Action',
    description: 'Batman faces a dangerous criminal known as the Joker.'
  },
  {
    id: 3,
    title: 'Interstellar',
    year: 2014,
    genre: 'Science Fiction',
    description: 'Explorers travel through space looking for a new home.'
  },
  {
    id: 4,
    title: 'Avengers: Endgame',
    year: 2019,
    genre: 'Superhero',
    description: 'The Avengers attempt to undo the events caused by Thanos.'
  },
  {
    id: 5,
    title: 'The Matrix',
    year: 1999,
    genre: 'Science Fiction',
    description: 'A hacker discovers that reality is not what it seems.'
  }
]
const route = useRoute()
const movieId = Number(route.params.id)
const movie = movies.find(item => item.id === movieId)
</script>
<template>
  <section v-if="movie" class="details">
    <h2 class="page-title">{{ movie.title }}</h2>
    <p><strong>Year:</strong> {{ movie.year }}</p>
    <p><strong>Genre:</strong> {{ movie.genre }}</p>
    <p><strong>Description:</strong> {{ movie.description }}</p>
    <NuxtLink class="button" to="/items">
      ← Back to Movies
    </NuxtLink>
  </section>
  <section v-else class="not-found">
    <h2 class="page-title">Movie Not Found</h2>
    <p>
      The movie with ID {{ route.params.id }} does not exist.
    </p>
    <NuxtLink class="button" to="/items">
      ← Back to Movies
    </NuxtLink>
  </section>
</template>