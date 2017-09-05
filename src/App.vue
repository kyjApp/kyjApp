<template>
  <div id="app">
    <view-box>
      <x-header
      title="客有家租房"
      :left-options="{showBack:false}"
      slot="header">

      </x-header>

      <search></search>
      <tabbar slot="bottom">
        <tabbar-item>
          <img src="./assets/icon_nav_button.png" alt="" slot="icon">
          <span slot="label">所有房源</span>
        </tabbar-item>
        <tabbar-item>
          <img src="./assets/icon_nav_cell.png" alt="" slot="icon">
          <span slot="label">可租房源</span>
        </tabbar-item>
      </tabbar>
    </view-box>
    <!-- <router-view></router-view> -->
  </div>
</template>

<script>
import {ViewBox, XHeader, Tabbar, TabbarItem} from 'vux'
import search from './components/search'
export default {
  name: 'app',
  components: {
    ViewBox,
    XHeader,
    Tabbar,
    TabbarItem,
    search
  }
}
</script>

<style>
/*@import '~vux/src/styles/reset.less';*/
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /*margin-top: 60px;*/
}
#app{
  height:100%;
}
html,body{
  margin:0;
  padding:0;
  width:100%;
  height:100%;
}
</style>
