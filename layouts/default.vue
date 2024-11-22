<template>
  <div class="wrapper">
    <slot />
  </div>
</template>

<script setup></script>

<style scoped>
.wrapper {
  min-height: 100vh;
  width: 100%;
}
.main {
  min-height: calc(100vh - 56px - 281px);
}
</style>
