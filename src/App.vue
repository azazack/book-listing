<script setup lang="ts">
import { ref } from "vue";
import BookCard from "../src/components/BookCard.vue";
import Loader from "../src/components/loader.vue";
import Pagination from "../src/components/pagination.vue";
const term = ref(" ");

const List = ref([]);

const page = ref(1);

const loading = ref(false);

function fetchData() {
  loading.value = true;
  const apiUrl = `https://goodreads-server-express--dotdash.repl.co/search/${term.value}?page=${page.value}`;

  fetch(apiUrl)
    .then((res) => {
      return res.json();
    })
    .then((resJson) => {
      List.value = resJson.list;
    })
    .catch(() => {
      List.value = []
      console.log(List.value)
    })
    .finally(() => {
      loading.value = false;
    });
}

function previous() {
  page.value--;
  fetchData();
}

function next() {
  page.value++;
  fetchData();
}
</script>

<template>
  <div class="container py-4">
    <div class="row pb-3">
      <div class="col-4">
        <input
          type="text"
          v-model="term"
          class="form-control flex-grow-1"
          @keyup.enter="fetchData"
        />
      </div>
      <div class="col-2">
        <button @click="fetchData" class="form-control">Search</button>
      </div>
    </div>
    <div class="text-center" v-if="loading">
      <Loader />
    </div>
    <div class="row" v-else-if="List.length">
      <div class="col-3 mb-3" v-for="book in List">
        <BookCard :book="book"></BookCard>
      </div>
    <Pagination @next="next" @previous="previous"></Pagination>
    </div>
    <div class="text-center" v-else>Feel free to type to search for books</div>
  </div>
</template>

<style scoped></style>
