<template>
  <div class="row map">
    <!-- <h2>center is {{currentCenter}}, zoom is {{currentZoom}}</h2> -->
    <l-map @update:center="centerUpdate" @update:zoom="zoomUpdate" :zoom="zoom" :center="center">
      <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
      <l-marker
        :key="index"
        v-for="(brew, index) in brews"
        :lat-lng="latLng(brew.latitude, brew.longitude)"
      >
        <l-icon :icon-size="brew.iconSize" :icon-url="icon"></l-icon>
      </l-marker>
    </l-map>
  </div>
</template>

<script>
import { LMap, LTileLayer, LMarker, LIcon } from "vue2-leaflet";
import logo from "../assets/logo.png";

export default {
  name: "Map",
  props: {
    brews: Array
  },
  components: {
    LMap,
    LTileLayer,
    LMarker,
    LIcon
  },
  data() {
    return {
      zoom: 7,
      // the commented one is centre HK
      // center: L.latLng(22.352, 114.17),
      center: L.latLng(33.74, -112.17),
      currentCenter: L.latLng(33.74, -112.17),
      currentZoom: 7,
      url:
        // do not make any commit to a public repo with YOUR OWN API KEY inside!
        "https://tile.thunderforest.com/cycle/{z}/{x}/{y}.png?apikey=",
      attribution:
        'Maps &copy; <a href="https://www.thunderforest.com/">Thunderforest</a>, Data &copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      marker: L.latLng(22.352, 114.17),
      icon: logo,
      iconSize: [25, 25]
    };
  },
  methods: {
    latLng: function(lat, lng) {
      return L.latLng(lat, lng);
    },
    centerUpdate: function(center) {
      this.currentCenter = center;
    },
    zoomUpdate: function(zoom) {
      this.currentZoom = zoom;
    }
  }
};
</script>

<style scoped>
.map {
  height: 100%;
}
</style>
