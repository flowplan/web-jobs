<template>
  <h1>Jobs</h1>
  <div v-if="jobs.length">
    <!-- Format for if data not appear yet -->
  <div v-for="job in jobs" :key="job.key" class="job">
    <!-- Routing Format with Dynamic just add params you have -->
    <router-link :to="{ name: 'JobDetails', params: { id: job.id }}">
      <h2>{{ job.title }}</h2>
    </router-link>
  </div>
  </div>
  <div v-else>
    <p>Loading Jobs...</p>
  </div>
</template>

<script>
export default {
    data(){
        return{
            jobs:[]

            // jobs: [
            //     {title: 'UX Developer', id: 1, details: 'lorem'},
            //     {title: 'Web Developer', id: 2, details: 'lorem'},
            //     {title: 'Vue Developer', id: 3, details: 'lorem'}
            // ]
        }
    },
    mounted(){ //Onload
      fetch("http://localhost:3000/jobs")
      .then(res => res.json())
      .then(data => this.jobs = data)
      .catch(err => console.log(err.message))
      //Fetch a json data
    }
}
</script>

<style>
.job h2{
  background-color: #f4f4f4;
  padding: 20px;
  border-radius: 10px;
  margin: 10px auto;
  max-width: 600px;
  cursor: pointer; 
  color: #444;  
}
.job h2:hover{
  background: #ddd;
}
.job a{
  text-decoration: none;
}
</style>