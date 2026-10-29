<template>
  <div class="site">
    <header class="header">
      <h1>Movie Catalogue</h1>
      <nav class="nav">
        <NuxtLink to="/">Home</NuxtLink>
        <NuxtLink to="/about">About</NuxtLink>
        <NuxtLink to="/items">Movies</NuxtLink>
      </nav>
    </header>
    <main class="content">
      <slot />
    </main>
    <footer class="footer">
      <p>© 2026 Movie Catalogue</p>
    </footer>
  </div>
</template>