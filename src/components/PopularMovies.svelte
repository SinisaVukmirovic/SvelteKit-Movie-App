<script>
    import MovieCard from './MovieCard.svelte';
    export let popular; 
</script>

<h2>Popular Movies</h2>

<div class="popular-movies">
    {#each popular as movie}
        <MovieCard {movie} />
    {/each}
</div>

<style>
    h2 {
        padding: 0 1rem;
    }
    .popular-movies {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        grid-gap: 2rem 1rem;
    }
</style>