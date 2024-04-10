<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <header>
    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav class="navMenu">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/register">Registro</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>
