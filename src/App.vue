<script setup>
import { ref } from "vue";
import PostsCard from "./components/PostsCard.vue";
import PaginationBtns from "./components/PaginationBtns.vue";

const arrayPosts = ref([]);
const favorite = ref("");

const next = 10;
const start = ref(0);
const end = ref(10);

const nextPage = () => {
  start.value = start.value + next;
  end.value = end.value + next;
};

const prevPage = () => {
  start.value = start.value - next;
  end.value = end.value - next;
};

const marcarFavorito = (title) => {
  favorite.value = title;
};

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
    <h3>
      Favorito: <span class="fst-italic">{{ favorite }}</span>
    </h3>
    <PaginationBtns @nextPage="nextPage" @prevPage="prevPage" :arrayLenght="arrayPosts.length" :start="start" :end="end"/>
    <PostsCard
      v-for="item in arrayPosts.slice(start, end)"
      :key="item.id"
      v-bind="item"
      @newFavorite="marcarFavorito"
    />
  </div>
</template>
