<template>
  <li v-bind:class="{ active: title.isActive }">{{ title.name }}</li>
</template>

<script>
export default {
  name: 'MenuButton',
  props: {
    title: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

li {
  display: inline-block;
  list-style-type: none;
  padding: 7px;
  margin: 10px;
  width: 130px;
  height: 40px;
  border-radius: 15px;
  background-color: #e1e1e1;
  text-align: center;
  cursor: pointer;
}
.active {
  background-color: #27e9b6;
  color: #fff;
}

</style>
