<template>
  <div class="flex flex-row">
    <div class="basis-64">
      <NamePlate class="nameplate" />
    </div>
  </div>
</template>

<script setup lang="ts">
  import NamePlate from './assets/ef-nameplate.svg'
</script>

<style scoped>
  .nameplate {
    width: 100%;
    height: auto;
    display: block;
    margin: 0 auto;
  }
</style>