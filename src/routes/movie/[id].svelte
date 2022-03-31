<script context="module">
    export async function load({ fetch, params }) {
        // const apiUrl = 'https://api.themoviedb.org/3/movie/popular?api_key=6022a4ae03ca3a0275414b787f65b604';
        const apiUrl = `https://api.themoviedb.org/3/movie/${params.id}?api_key=6022a4ae03ca3a0275414b787f65b604&language=en-US`;
        const res = await fetch(apiUrl);
        const movieDetail = await res.json();

        if (res.ok) {
            return {
                props: { movieDetail }
            }
        }
    }
</script>

<script>
import { mode } from "$app/env";
    import { fly } from 'svelte/transition';

    export let movieDetail;
</script>

<div class="movie-details" in:fly={{x: 200, duration: 500, delay:500}}>
    <div class="img-container">
        <img src={`https://image.tmdb.org/t/p/original${movieDetail.backdrop_path}`} alt={movieDetail.title}>
    </div>
    <div class="text-container">
        <h2>{movieDetail.title}</h2>
        <p class="overview">{movieDetail.overview}</p>
        <p>
            <span>Release Date: </span>{movieDetail.release_date} <br />
            <span>Ratings: </span>{movieDetail.vote_average} <br />
            <span>Runtime: </span>{movieDetail.runtime} mins
        </p>
    </div>
</div>

<style>
    .img-container {
        width: 100%;
    }
        img {
            width: 100%;
            border-radius: 1rem;
        }
    .movie-details {
        margin: 2rem 20%;
    }
    .text-container {
        padding: .5rem 3rem;
    }
    p {
        padding: 1rem 0;
    }
    span {
        font-weight: bold;
    }
</style>