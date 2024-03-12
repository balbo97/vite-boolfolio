<script>
import { store } from '../store';
export default {

   name: 'SingleProjects',
   props: {
    project: Object,
   },
   data() {
    return {
       store
    }
   },
   methods: {
    createSubstr(){
        return this.project.content.substr(0, 70) + "...";
    }
   },
}
</script>

<template lang="">
    <div class="col-4">

        <div class="card my-2">
            <img :src="`${store.baseUrl}/storage/${project.cover_image}`" class="card-img-top" alt="...">
            <div class="card-body">
                <h5 class="card-title">{{project.title}}</h5>
                <p>{{createSubstr()}}</p>
               
            </div>
        </div>
    </div>
   
</template>

<style lang="scss">
@use '../styles/generals.scss' as *;


</style>