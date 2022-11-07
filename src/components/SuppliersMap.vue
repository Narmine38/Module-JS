<template>
  <div>
    <h3>Carte des fournisseurs</h3>
    <div style="height: 80vh">
      <LMap :zoom="zoom" :center="center">
        <LTileLayer :url="url"></LTileLayer>
        <l-marker v-for="supplier in info.data.data" v-bind:key="supplier.id" v-bind:lat-lng="[supplier.latitude,supplier.longitude]" />
      </LMap>
    </div>
  </div>

</template>

<script>
import {LMap, LTileLayer, LMarker} from "vue2-leaflet";
import axios from "axios";

export default {
  name: "MapMap",
  components: {
    LMap,
    LTileLayer,
    LMarker
  },
  data() {
    return {
      url: "https://{s}.tile.osm.org/{z}/{x}/{y}.png",
      zoom: 6,
      center: [46.5322, 2.9482],
      bounds: null,
      info: [],
      loading: true,
      error: false

    };
  },
  mounted() {
    axios
        .get('https://heroku-campus-suppliers.herokuapp.com/api/suppliers')
        .then(response => (this.info = response))
        .catch(error => {
          console.log(error)
          this.errored = true
        })
        .finally(() => this.loading = false)
  }
};
</script>

<style scoped>

</style>