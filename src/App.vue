<template>
  <div id="app">
    <view-box>
      <x-header
      title="客有家租房"
      :left-options="{showBack:false}"
      slot="header"
      class="header">
      </x-header>
      <search class="search"></search>
      <scroller
        :on-refresh="refresh"
        refresh-text="loading"
        :on-infinite="infinite"
        ref="myRef"
       >
       <panel :list="dataList" :type="type" class="panel"></panel>
       <panel :list="moreDataList" :type="type" class="panel panel1"></panel>
      </scroller>
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
var refreshKey = ['A', 'B01', 'B02']
var key = 0
var start = 0
var end = start + 9
var keyValue = 'A'
var initloaded = false // 初始化数据是否加载完成
function getRefreshKey () {
  key++
  if (key == refreshKey) {
    key = 0
  }
  keyValue = refreshKey[key]
}
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
      dataList: dataList,
      moreDataList: []
    }
  },
  methods: {
    refresh () {
      // 下拉刷新
      getRefreshKey()
      this.$jsonp('http://3g.163.com/touch/jsonp/sy/recommend/0-9.html', {
        miss: '00',
        refresh: keyValue
      }).then(data => {
        console.log(data, 'data数据')
        // 刷新数据
        this.dataList = data.list.filter(item => {
          return item.addata === null && item.picInfo.length
        }).map(item => {
          return {
            src: item.picInfo[0].url,
            title: item.title,
            desc: item.digest,
            url: item.link
          }
        })
        this.$refs.myRef.finishPullToRefresh()
        this.$vux.toast.text(`当前一共刷新了${this.dataList.length}条数据`, 'top')
      })
    },
    infinite () {
      // if (!initloaded) {
      //   this.$refs.myRef.finishInfinite()
      //   return
      // }
      console.log(2)
      this.$jsonp(`http://3g.163.com/touch/jsonp/sy/recommend/${start}-${end}.html`, {
        miss: '00',
        refresh: keyValue
      }).then(data => {
        // 上拉加载更多
        setTimeout(() => {
          this.dataList = data.list.filter(item => {
            return item.addata === null
          }).map(item => {
            return {
              src: item.picInfo[0].url,
              title: item.title,
              desc: item.digest,
              url: item.link
            }
          })
          this.moreDataList = this.moreDataList.concat(this.dataList)
          start += 10
          end = start + 9
          this.$refs.myRef.finishInfinite()
        }, 1000)
      })
      // http://3g.163.com/touch/jsonp/sy/recommend/'+start+'-'+end+'.html'
    }
  }
}
</script>

<style lang="less">
@import '~vux/src/styles/reset.less';
html,body{
  margin:0;
  padding:0;
  width:100%;
  height:100%;
  overflow: hidden;
}
a{
  text-decoration: none;
}
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
#app .panel1{
  margin:0;
}
._v-container>._v-content>.active[data-v-ecaca2b0]{
  margin-top:-60px;
}
</style>
