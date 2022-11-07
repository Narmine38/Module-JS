<template>
<div>

</div>
</template>

<script>
import axios from "axios";

export default {
  name: "SkillsMe",

  mounted() {
    axios
        .get('https://app.campus-skills.com/xq595RG9EhACiZ98N/students/mbf9o23HjLFG6sorD/skills')
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