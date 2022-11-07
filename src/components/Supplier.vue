<template>
  <div class="card">
    <h5 class="card-header">{{ name }}</h5>
    <div class="card-body">
      <h5 style="color: red" v-if="status === false" class="card-title">
        A du stock ? KO
      </h5>
      <h5 v-else style="color: green" class="card-title">
        A du stock ? OK
      </h5>
      <p class="card-text">Date de dernière des stocks: {{checkedAt}}</p>
      <p>latitude: {{latitude}} longitude: {{longitude}}</p>
    </div>
  </div>

</template>

<script>
export default {
  name: "SupplierCompo",
  props:{
    name: String,
    status: Boolean,
    checkedAt: String,
    latitude: String,
    longitude: String
  },
}
</script>
getelemeh5è
<style scoped>

</style>