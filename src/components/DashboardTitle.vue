<template>
  <div>
    <span class="dashboard__title">{{mainTitle}}</span>
    <span v-if="subTitleDark" class="dashboard__subtitle dashboard__subtitle-dark">{{subTitleDark}}</span>
    <span class="dashboard__subtitle">{{subTitle}}</span>
    <i class="material-icons dashboard__more">more_vert</i>
  </div>
</template>

<script>
export default {
  name: 'DashboardTitle',
  props: {
    mainTitle: String,
    subTitleDark: String,
    subTitle: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.dashboard__title {
  font-size: 28px;
  padding-right: 20px;
}
.dashboard__subtitle {
  color: #939598;
}
.dashboard__subtitle-dark {
  color: #58595b;
  padding-right: 20px;
}
.dashboard__more {
  float: right;
  color: #e1e1e1;
  margin-top: 10px;
  cursor: pointer;
}

</style>
