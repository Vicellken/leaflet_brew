<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-12">
        <h1 class="text-center text-info">Breweries List</h1>
      </div>
      <!-- /.col-12 -->
    </div>
    <br />
    <!-- /.row -->
    <div class="row">
      <div class="col-6">
        <!-- use BrewList -->
        <BrewList v-bind:brews="brews" />
      </div>
      <div class="col-6">
        <Map v-bind:brews="brews"/>
      </div>
    </div>
    <!-- /.row -->
    <br />
    <br />
    <div class="jumbotron">
      <h1 class="display-4">Hello, world!</h1>
      <p
        class="lead"
      >This is a simple hero unit, a simple jumbotron-style component for calling extra attention to featured content or information.</p>
      <hr class="my-4" />
      <p>It uses utility classes for typography and spacing to space content out within the larger container.</p>
      <a class="btn btn-primary btn-lg" href="#" role="button">Learn more</a>
    </div>
  </div>
  <!-- /.container -->
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
      brews: []
    };
  },
  mounted() {
    axios
      .get("https://api.openbrewerydb.org/breweries")
      .then(response => 
      (this.brews = response.data.filter(response =>
      response.state == 'Arizona'))
      );
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
</style>
