<template>
  <div>
    <div id="map"></div>
  </div>
</template>
<script>
import { Scene } from "@antv/l7";
import { GaodeMap } from "@antv/l7-maps";
import { DrawControl } from "@antv/l7-draw";
export default {
  data() {
    return {};
  },
  mounted() {
    const scene = new Scene({
      id: "map",
      map: new GaodeMap({
        pitch: 0,
        style: "light",
        layers: [],
        center: [87.629, 43.94809506708969],
        zoom: 50
      })
    });

    const layer1 = new AMap.TileLayer.Satellite();
    scene.map.setLayers([]);
    layer1.setMap(scene.map);
    const drawControl = new DrawControl(scene, {
      position: "topright",
      layout: "horizontal", // horizontal vertical
      controls: {
        point: true,
        polygon: true,
        line: true,
        circle: true,
        rect: true,
        delete: true
      }
    });
    scene.addControl(drawControl);
  }
};
</script>
<style>
/* ::-webkit-scrollbar {
  display: none;
}

html,
body {
  overflow: hidden;
  margin: 0;
}

#map {
  position: absolute;
  top: 0;
  bottom: 0;
  width: 100%;
} */
</style>