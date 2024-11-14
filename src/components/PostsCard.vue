<script setup>
const props = defineProps({
  id: Number,
  title: String,
  body: String,
  userId: Number,
});

const emit  = defineEmits(["newFavorite"])
</script>

<template>
  <div class="card m-3">
    <div class="body-card p-5">
      <h5 class="card-title fw-bold">{{ id }} .- {{ title }}</h5>
      <p>{{ body }}</p>
      <button class="btn btn-danger" @click="emit('newFavorite', title)">Agregar a favoritos</button>
    </div>
  </div>
</template>
