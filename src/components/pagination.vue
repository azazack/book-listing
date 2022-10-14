<template>
  <div class="d-flex justify-content-center">
    <nav aria-label="Page navigation example">
      <ul class="pagination">
        <li class="page-item">
          <a class="page-link" @click="$emit('previous')">Previous</a>
        </li>
        <li class="page-item">
          <a class="page-link" @click="$emit('next')">Next </a>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script lang="ts" setup>
</script>
