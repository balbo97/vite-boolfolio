<script>
export default {
    data() {
        return {
            navLinks: [
                {
                    name: 'home',
                    label: 'Home',
                },
                {
                    name: 'projects',
                    label: 'Projects',
                },
                {
                    name: 'contact',
                    label: 'Mail us!',
                },
            ],

        };
    },
    created() {

    },
    methods: {

    },
}
</script>

<template>
    <header>
        <div class="container">
            <div class="row">
                <div class="col-12 d-flex justify-content-between align-items-center py-3">
                    
                    <h1>BoolFolio</h1>
                    <div class="links">

                        <ul class="list-unstyled d-flex">
                            
                            <li class=" mx-2" v-for="link, index in navLinks">
                                <a :href="{ name: link.name }" class="link-underline link-underline-opacity-0" >{{ link.label }}</a>
                                
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </header>
   
        

</template>

<style scoped lang="scss">
@use '../styles/generals.scss' as *;

header{
    background-color: grey;
}
</style>