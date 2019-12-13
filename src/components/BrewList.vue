<template>
  <div class="card brew-list" style="width: 30rem;">
    <div class="card-header">Available Breweries</div>
    <ul class="list-group list-group-flush">
      <li v-for="brew in brews" :key="brew.id" class="list-group-item">{{brew.name}}, {{brew.state}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "BrewList",
  props: {
    brews: Array
  }
};
</script>

<style lang="scss" scoped>
.brew-list {
  overflow-y: scroll;
  height: 95vh;
  li {
    &:hover {
      background-color: darkgray;
    }
  }
}
</style>