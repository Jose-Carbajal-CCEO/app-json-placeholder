<script setup>
const emit = defineEmits(["prevPage", "nextPage"]);
const props = defineProps(["arrayLenght", "start", "end"]);
</script>

<template>
  <div class="d-flex justify-content-around p-2">
    <button
      class="btn btn-primary"
      @click="emit('prevPage')"
      :disabled="start <= 0"
    >
      Previous page
    </button>
    <button
      class="btn btn-primary"
      @click="emit('nextPage')"
      :disabled="end >= arrayLenght"
    >
      Next one
    </button>
  </div>
</template>
