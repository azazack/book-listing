<script lang="ts" setup>
interface props {
  book: {
    title: String;
    authorName: String;
    imageUrl: String;
  };
}
const props = defineProps<props>();
</script>

<template>
  <div class="book-card p-2">
    <div class="text-center">
      <img :src="props.book.imageUrl" alt="" />
    </div>
    <div class="mt-2">
      <p class="text-truncate m-0 fw-bold" :title="props.book.title">
        {{ props.book.title }}
      </p>
      <span class="fw-light text-secondary">{{ props.book.authorName }}</span>
    </div>
  </div>
</template>

<style lang="scss">
.book-card {
  border: 1px solid #eeedbe;
  border-radius: 4px;
  box-shadow: rgba(99, 99, 99, 0.2) 0 2px 8px 0;
  height: 250px;
}
</style>
