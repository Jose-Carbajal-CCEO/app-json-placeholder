<script setup>
const props = defineProps({
  id: Number,
  title: String,
  body: String,
  userId: Number,
});
</script>

<template>
  <div class="card m-3">
    <div class="body-card p-5">
      <h5 class="card-title fw-bold">{{ id }} .- {{ title }}</h5>
      <p>{{ body }}</p>
    </div>
  </div>
</template>
