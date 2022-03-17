<script>
    export let movie;
</script>

<div class="movie-card">
    <a href={`/movie/${movie.id}`}>
        <img src="{`https://image.tmdb.org/t/p/w300${movie.poster_path}`}" alt={movie.title}>
    </a>
    <div class="description">
        <h3>{movie.title}</h3>
        <p>{movie.release_date}</p>
    </div>
</div>


<style>
    img {
        width: 100%;
        /* height: 35vh; */
        object-fit: cover;
        border-radius: 1rem;
    }
    h3 {
        font-size: .9rem;
    }
    .description {
        height: 5vh;
    }
    p {
        font-size: .7rem;
    }
    .movie-card {
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        padding: 1rem .5rem;
    }
</style>