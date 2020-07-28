<template>

    <div>

        <h1>Using The Movie Database API - Movie Search with Axios</h1>

        <hr>

        <input class="searchBar" type='text' v-model='query' @keyup='getResult(query)'>

        <hr>

        <div class="d-flex flex-wrap flex-row justify-content-center align-items-center">
            <div class="card" v-for='result in results' :key='result.id'>
                <img class="card-img-top" :src="'http://image.tmdb.org/t/p/w500/' + result.poster_path">
                <div class="card-body">
                    <h6>Movie Name: {{ result.original_title }}</h6>
                    <h6>Release Date: {{ result.release_date }}</h6>
                </div>
            </div>
        </div>



    </div>

</template>



<script>

    import axios from 'axios'

    export default {

        name: "Search",

        data(){
            return{
                query : '',
                results: '',
            }
        },

        methods : {
            getResult(query){
                axios.get('https://api.themoviedb.org/3/search/movie?api_key=[TMDB API KEY]&query=' + query)
                    .then(response => {
                        this.results = response.data.results
                    });
                console.log(this.results)
            },
        },



    }
</script>



<style>

    .card {
        width: 300px;
        margin: 10px;
    }

    .searchBar {
        width: 300px;
    }



</style>