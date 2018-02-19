<template>
  <div class="searchWrap">
    <input type="text" class="search" placeholder="Searching here..." />
    <i class="material-icons">search</i>
  </div>
</template>

<script>
export default {
  name: 'Search'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.search {
  width: 100%;
  background-color: #fff;
  outline: none;
  border-radius: 15px;
  padding: 5px 20px;
  border: 1px solid #e1e1e1;
}

.search::placeholder {
  color: #ebebeb;
  font-size: 14px;
}
.searchWrap {
  position: relative;
}
.searchWrap i {
  position: absolute;
  top: 50%;
  right: 10px;
  transform: translateY(-50%);
  color: #ebebeb;
}
</style>
