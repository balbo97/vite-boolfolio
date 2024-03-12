<script>
import { store } from '../store.js';
import axios from 'axios';
import SingleProject from './SingleProject.vue';

export default {

   name: 'AppMain',
   components: {
        SingleProject
   },
   data() {
    return {
        store, 
        projects: []
    }
   },
   created() {
    this.getProjects();
   },
   methods: {
    getProjects(){
        axios.get(`${this.store.baseUrl}/api/projects`).then((response) =>{
            console.log(response.data.results)
            this.projects = response.data.results
        })
    }
   }
}
</script>

<template lang="">
    <div>
        <div class="container">

            <div class="row">
                <div class="col-12 my-3 text-center text-danger">
                    <h1>My Projects:</h1>
                </div>
            </div>
            <div class="row">
                
                <!-- Projects -->
                <SingleProject v-for="project, index in projects" :key="index" :project= "project"/>
            </div>
        </div>

    </div>
</template>

<style lang="scss">
@use '../styles/generals.scss' as *;


</style>