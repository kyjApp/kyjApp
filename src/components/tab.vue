<template>
  <div class="rows">
      <div class="list">
        <a href="javascript:;">区域<span></span></a>
        <ul class="listOpt">
          <li>长安区</li>
          <li>长安区</li>
          <li>长安区</li>
          <li>长安区</li>
          <li>长安区</li>
        </ul>
      </div>
      <div>
        <a href="javascript:;">价格<span></span></a>
        <ul class="listOpt">
          <li>长安区</li>
          <li>长安区</li>
          <li>长安区</li>
          <li>长安区</li>
          <li>长安区</li>
        </ul>
      </div>
      <div>
        <a href="javascript:;">合租<span></span></a>
        <ul class="listOpt">
          <li>长安区</li>
          <li>长安区</li>
          <li>长安区</li>
          <li>长安区</li>
          <li>长安区</li>
        </ul>
      </div>
      <div>
        <a href="javascript:;">户型<span></span></a>
        <ul class="listOpt">
          <li>长安区</li>
          <li>长安区</li>
          <li>长安区</li>
          <li>长安区</li>
          <li>长安区</li>
        </ul>
      </div>
      <div class="mask"></div>
  </div>
</template>

<script>
export default {
  data () {
    return {}
  }
}
</script>

<style>

a {
  text-decoration: none;
}
ul{
  padding:0;
}

.rows{
  display: flex;
  margin-top:90px;
}
.rows div{
  width:0;
  flex-grow: 1;
  margin:auto;
}
.rows div a{
  font-size:14px;
  color:#666;
  text-align: center;
  line-height: 45px;
  display: block;
  border-bottom:1px solid #e9e9e9;
}
.rows div a span{
  display: inline-block;
  width:11px;
  height:7px;
  background-image:url(../assets/arrow.png);
  background-size: 11px 7px;
  margin-left:20px;
}
.rows .listOpt{
  position:absolute;
  top:136px;
  left:0;
  width: 100%;
  z-index: 66;
  padding:0;
}
.rows .listOpt li{
  list-style-type: none;
  font-size: 14px;
  text-align: center;
  line-height: 45px;
  background-color: #fff;
  border-bottom: 1px solid #e9e9e9;
  margin: 0 auto;
}
.rows .mask{
  position: absolute;
  top: 136px;
  left: 0%;
  width: 100%;
  height: 100%;
  background: black;
  z-index: 55;
  opacity: .7;  
}
</style>
