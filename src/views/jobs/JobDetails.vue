<template>
  <div v-if="job">
    <h1>{{ job.title }}</h1>
    <p>{{ job.details }}</p>

    <p>The job id is {{ id }}</p>
    <!-- <p>The job id is {{ $route.params.id }}</p> -->
  </div>
  <div v-else>
    <p>Loading job details...</p>
  </div>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      // id: this.$route.params.id
      job: null,
    };
  },
  mounted() {
    fetch("http://localhost:3000/jobs/" + this.id)
      .then((res) => res.json())
      .then((data) => (this.job = data))
      .catch((err) => console.log(err.massage));
  },
};
</script>

<style>
</style>