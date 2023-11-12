<script setup>
import showLists from './components/RestaurantList.vue';
</script>

<template>
  <div id="app">
    <header>
      <div class="wrapper">
        <showLists />
      </div>
    </header>


  </div>
</template>

<style scoped>
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

</style>
