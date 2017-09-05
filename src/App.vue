<template>
  <div id="app">
    <view-box></view-box>
    <!-- <router-view></router-view> -->
  </div>
</template>

<script>
import {ViewBox} from 'vux'
export default {
  name: 'app',
  components: {
    ViewBox
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
