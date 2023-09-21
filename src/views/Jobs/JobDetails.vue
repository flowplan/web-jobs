<template>
<!-- Format of fetching data -->
<div v-if="job">
  <h1>{{ job.title }}</h1>
  <p>This job id is {{ this.id }}</p>
  <p>{{ this.details }}</p>
</div>
<div v-else>
  <p>Loading Job Details...</p>
</div>
</template>

<script>
export default {
    props: [ 'id' ],
    data(){
      return{
        job: null
      }
    },
    mounted(){//onload
       fetch("http://localhost:3000/jobs/" + this.id)
      .then(res => res.json())
      .then(data => this.job = data)
      .catch(err => console.log(err.message))
    }
    // data(){
    //     return{
    //         id: this.$route.params.id
    //     }
    // }
}
</script>

<style>

</style>