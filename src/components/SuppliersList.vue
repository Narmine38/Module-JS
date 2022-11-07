<template>
  <div>
    <h3>Liste des fournisseurs</h3>
    <Supplier v-for="supplier in info.data.data" v-bind:key="supplier.id" v-bind:name="supplier.name"
              v-bind:status="supplier.status" v-bind:checked-at="format(new Date())" v-bind:latitude="supplier.latitude" v-bind:longitude="supplier.longitude"/>
  </div>

</template>

<script>
import {format} from 'timeago.js';
import Supplier from "@/components/Supplier";
import axios from "axios";

export default {
  name: "SuppliersList",
  components: {Supplier},
  data() {
    return {
      format,
      info: [],
      loading: true,
      error: false
    }
  },
  mounted() {
    axios
        .get('http://heroku-campus-suppliers.herokuapp.com/api/suppliers')
        .then(response => (this.info = response))
        .catch(error => {
          console.log(error)
          this.errored = true
        })
        .finally(() => this.loading = false)
  }
}
</script>

<style scoped>

</style>