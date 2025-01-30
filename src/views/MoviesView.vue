<template>
    <div class="outer-wrapper">
        <AddMovie @movieAdded="getMovies()" />
        
        <div class="movie-wrapper">
            <p>Klicka på en film för att ta bort den</p>
            <Movie @deleteMovie="deleteMovie(movie.id)" v-for="movie in movies" :movie="movie" :key="movie.id" />
        </div>
    </div>
</template>

<script>
import Movie from "../components/Movie.vue";
import AddMovie from "../components/AddMovie.vue";

export default {
    data() {
        return {
            movies: []
        }
    },
    components: {
        Movie,
        AddMovie
    },
    methods: {
        async getMovies() {
            const response = await fetch("https://moment2-fulllstack.onrender.com/movies");
            const data = await response.json()

            this.movies = data;
        },
        async deleteMovie(id) {
            const response = await fetch("https://moment2-fulllstack.onrender.com/movies/" + id, {
                method: "DELETE",
                headers: {
                    "Accept": "application/json",
                    "Content-type": "application/json"
                }
            });

            const data = await response.json();

            this.getMovies();
        }
    },
    mounted() {
        this.getMovies();
    }
}
</script>

<style>
.movie-wrapper {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-top: 50px;
}

.movie-wrapper>p {
    align-self: end;
}
</style>