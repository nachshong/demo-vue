<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router';
</script>

<template>
  <div>
    <RouterLink to="/">Home</RouterLink>
    &nbsp; | &nbsp;
    <RouterLink to="/products">Products</RouterLink>
    &nbsp; | &nbsp;
    <RouterLink to="/about">About</RouterLink>
  </div>
  <div>
    <RouterView />
  </div>
</template>