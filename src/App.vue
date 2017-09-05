<template>
  <div id="app">
    <view-box>
      <x-header
      title="客有家租房"
      :left-options="{showBack:false}"
      slot="header"
      class="header"></x-header>

      <search class="search"></search>

      <panel :list="dataList" :type="type" class="panel"></panel>

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
import {ViewBox, XHeader, Tabbar, TabbarItem, Panel} from 'vux'
import search from './components/search'
export default {
  name: 'app',
  components: {
    ViewBox,
    XHeader,
    Tabbar,
    TabbarItem,
    search,
    Panel
  },
  data () {
    var dataList = []
    for (var i = 0; i < 10; i++) {
      dataList.push({
        src: 'http://placeholder.qiniudn.com/60x60/3cc51f/ffffff',
        title: '玉泉营.万年花城二期',
        desc: '112m²/302/3居室',
        url: '/component/cell'
      })
    }
    return {
      type: '2',
      dataList: dataList
    }
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
  height:100%;
}
#app .header{
  position: absolute;
  width: 100%;
  top: 0px;
  left: 0;
  z-index: 9;
}
#app .search{
  position:fixed;
  top:46px;
  left:0;
  z-index:5;
  width:100%;
}
#app .panel{
  margin-top:90px;
}
html,body{
  margin:0;
  padding:0;
  width:100%;
  height:100%;
  overflow: hidden;
}
</style>
