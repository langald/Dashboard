<template>
  <div class="balloon">
    <div v-if="balloonData.topTitle" class="balloon__title">{{ balloonData.topTitle }}</div>
    <div class="balloon__value">{{ balloonData.value }}</div>
    <div class="balloon__title">{{ balloonData.title }}</div>
  </div>
</template>

<script>
export default {
  name: 'Ballon',
  props: {
    balloonData: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.balloon {
  display: inline-block;
}
.balloon__value {
  color:#58595b;
  font-size: 24px;
}
.balloon__title {
  color: #939598;
  font-size: 12px;
  letter-spacing: 2.2px;
}
</style>
