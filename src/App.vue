<template>
  <div class="wrapper">
    <div class="cards">
      <the-menu></the-menu>
      <the-chart></the-chart>
    </div>
  </div>
</template>

<script></script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}
</style>

<script>
import TheMenu from './components/TheMenu.vue';
import TheChart from './components/TheChart.vue';
export default{
  components: {
    TheMenu,
    TheChart
  }
}

</script>