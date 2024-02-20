<template>
    <main class="container">
        <div class="row">
            <div class="col-12">
                <ul>
                    <li v-for="project in projects" :key="project.id">
                        {{ project.title }}
                    </li>
                </ul>
            </div>
        </div>
    </main>
</template>
<script>
import axios from 'axios';
export default {
    name: 'AppMain',
    data() {
        return {
            projects: []
        }
    },
    methods: {
        getProjects(){
            axios.get('http://127.0.0.1:8000/api/projects', {
                params: {
                }
            })
            .then((response) => {
                console.log(response.data.results);
                this.projects = response.data.results;

            })
            .catch(function (error) {
                console.warn(error);
            })
        } 
        },
    
    created() {
        this.getProjects();
    },
}
</script>
<style lang="scss" scoped>
    
</style>