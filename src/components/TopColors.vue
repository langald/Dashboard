<template>
  <div class="topColors">
    <div class="topColors__color" :style="{ backgroundColor:  topColorsData.bgColor}"></div>
    <div class="topColors__title">{{ topColorsData.title }}</div>
    <div class="topColors__value">{{ topColorsData.value }}</div>
  </div>
</template>

<script>
export default {
  name: 'TopColors',
  props: {
    topColorsData: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.topColors {
  display: inline-block;
  text-align: center;
}
.topColors__color {
  width: 45px;
  height: 45px;
  border-radius: 10px;
  margin: 0 auto;
  margin-bottom: 10px;
}
.topColors__title {
  color: #939598;
  font-size: 12px;
  letter-spacing: 2.2px;
}
.topColors__value {
  color: #939598;
  font-size: 12px;
}
</style>
