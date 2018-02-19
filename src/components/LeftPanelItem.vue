<template>
  <div class="leftMenuItem" :style="{ backgroundColor:  leftMenuItem.bgColor}">
    <img v-if="leftMenuItem.src" :src="leftMenuItem.src" class="leftMenuItem__img" />
    <i v-else class="leftMenuItem__img material-icons">more_horiz</i>
  </div>
</template>

<script>
export default {
  name: 'LeftPanelItem',
  props: {
    leftMenuItem: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.leftMenuItem {
  position: relative;
  display: block;
  border-radius: 50%;
  width: 47px;
  height: 47px;
  background-color: #e1e1e1;
  color: #fff;
  margin: 20px auto;
  cursor: pointer;
}
.leftMenuItem__img {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 28px;
  height: auto;
}

</style>
