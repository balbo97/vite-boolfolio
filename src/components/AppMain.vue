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
        projects: [],
        currentPage : 1,
        lastPage : null
    }
   },
   created() {
    this.getProjects();
   },
   methods: {
    getProjects(pageNumber){
        axios.get(`${this.store.baseUrl}/api/projects`, {params:{page : pageNumber}}).then((response) =>{
            
            this.projects = response.data.results.data; 
            this.currentPage = response.data.results.current_page;
            this.lastPage = response.data.results.lastPage;
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
            <div class="row">
                <div class="col-12">
                    <div class="pagination-buttons text-center my-3">
                        <button class="btn btn-danger"  :class="currentPage = 1 ? 'disabled' : ''" @click="getProjects(currentPage -1)">Precedente</button>
                        <button class="btn btn-success ms-3" :class="currentPage = lastPage ? 'disabled' : ''" @click="getProjects(currentPage +1)">Successiva</button>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>

<style lang="scss">
@use '../styles/generals.scss' as *;


</style>