<template>
  <div class="row map">
    <l-map :zoom="zoom" :center="center">
      <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
      <l-marker
        :key="index"
        v-for="(brew, index) in brews"
        :lat-lng="latLng(brew.latitude, brew.longitude)"
      ></l-marker>
    </l-map>
  </div>
</template>

<script>
import { LMap, LTileLayer, LMarker } from "vue2-leaflet";

export default {
  name: "Map",
  props: {
    brews: Array
  },
  components: {
    LMap,
    LTileLayer,
    LMarker
  },
  data() {
    return {
      zoom: 7,
      // the commented one is centre HK
      // center: L.latLng(22.352, 114.17),
      center: L.latLng(33.74,-112.17),
      url:
        // do not make any commit to a public repo with YOUR OWN API KEY inside!
        "https://tile.thunderforest.com/cycle/{z}/{x}/{y}.png?apikey=10fdfaef484b4772bfa68b634b3a3853",
      attribution:
        'Maps &copy; <a href="https://www.thunderforest.com/">Thunderforest</a>, Data &copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      marker: L.latLng(22.352, 114.17)
    };
  },
  methods: {
    latLng: function(lat, lng) {
      return L.latLng(lat, lng);
    }
  }
};
</script>

<style scoped>
.map {
  height: 100%;
}
</style>