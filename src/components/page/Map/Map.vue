<template>
  <div class="map" style="height:100%;witdh:100%">
        <NavBar    fixed="true" title="地图" />
        <main class="main"  style="height:100%;witdh:100%">
           	<div id="allmap"></div>
        </main>
  </div>
</template>

<script>
import NavBar from '../../common/NavBar/NavBar.vue'
export default {
  name: 'map',
  data () {
    return {
   
    }
  },
  mounted(){
    this.setmap();
  },

  methods:{
   setmap(){
        var map = new BMap.Map("allmap");
        var point = new BMap.Point(116.404, 39.915);
        map.centerAndZoom(point, 15);
        // 编写自定义函数,创建标注
        function addMarker(point){
          var marker = new BMap.Marker(point);
          map.addOverlay(marker);
        }
        // 随机向地图添加25个标注
        var bounds = map.getBounds();
        var sw = bounds.getSouthWest();
        var ne = bounds.getNorthEast();
        var lngSpan = Math.abs(sw.lng - ne.lng);
        var latSpan = Math.abs(ne.lat - sw.lat);
        for (var i = 0; i < 5; i ++) {
          var point = new BMap.Point(sw.lng + lngSpan * (Math.random() * 0.7), ne.lat - latSpan * (Math.random() * 0.7));
          addMarker(point);
	      }
    }
  },
  components:{
      NavBar
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
#allmap{
  height:100%;
  width:100%;
}
</style>
