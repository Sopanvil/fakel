<script lang="ts" setup>
</script>

<template>
  <div class="main-container">
    <div class="container">
      <slot></slot>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.main-container {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  background: var(--main-bg-color);
  .container {
    width: 100%;
    max-width: 1340px;
    padding-top: 170px;
    margin: 0 20px;
  }
}
</style>
