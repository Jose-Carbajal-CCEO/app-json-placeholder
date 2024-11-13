<script setup>
import { ref } from "vue";
import PostsCard from "./components/PostsCard.vue";

const arrayPosts = ref([]);

const getData = async () => {
  try {
    const res = await fetch("https://jsonplaceholder.typicode.com/posts");
    const data = await res.json();
    arrayPosts.value = data;
  } catch (error) {
    console.log("Mamo esta cosa");
  }
};

getData();
</script>

<template>
  <div class="container">
    <h2 class="d-flex justify-content-center p-2 text-success fw-bold">
      Api json placeholder
    </h2>
    <PostsCard v-for="item in arrayPosts" :key="item.id" v-bind="item" />
  </div>
</template>
