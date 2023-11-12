<script setup>
import showLists from './components/RestaurantList.vue';
</script>

<template>
  <div id="app">
    <div class="wrapper">
      <show-lists />
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Roboto:100,300,400,500,700,900');
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: 'Roboto', sans-serif;
  font-weight: 300;
  font-size: 16px;
  line-height: 30px;
  color: #777;
}

.wrapper {
  width: 90%;
  margin: 0 auto;
  
}
</style>
