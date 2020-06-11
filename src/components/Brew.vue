<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-12">
        <h1 class="text-center text-info">Breweries List</h1>
      </div>
    </div>
    <br />

    <div class="row">
      <div class="col-4">
        <BrewList
          @mouse-over-brew="mouseOverBrew"
          @mouse-left-brew="mouseLeftBrew"
          v-bind:brews="brews"
        />
      </div>
      <div class="col-8">
        <Map v-bind:brews="brews" />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import BrewList from "./BrewList";
import Map from "./Map";

export default {
  name: "Brew",
  // after importing component, don't forget to register here
  components: {
    BrewList,
    Map
  },
  data() {
    return {
      brews: [],
      normalIcon: [25, 25],
      largeIcon: [80, 80]
    };
  },
  mounted() {
    axios.get("https://api.openbrewerydb.org/breweries").then(
      response =>
        (this.brews = response.data
          .filter(response => response.state == "Arizona")
          .map(response => {
            response.iconSize = this.normalIcon;
            return response;
          }))
    );
  },
  methods: {
    mouseOverBrew: function(index) {
      this.brews[index].iconSize = this.largeIcon;
    },
    mouseLeftBrew: function(index) {
      this.brews[index].iconSize = this.normalIcon;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
</style>
