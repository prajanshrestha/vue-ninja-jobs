<template>
  <div v-if="job">
    <h1>{{ job.title }}</h1> 
    <p>The job id is {{ id }}</p>
    <p>{{ job.details }}</p>
  </div>
  <div v-else>
    <p>Loading job details...</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  props: {
    id: {
      
    }
  },
  data() {
    return {
      // id: this.$route.params.id

      job: null
    }
  },
  mounted() {
    setTimeout(() => {
      axios
        .get("http://localhost:3000/jobs/" + this.id)
        .then((response) => {
          this.job = response.data
        })
    }, 500);
  }
}
</script>

<style>

</style>