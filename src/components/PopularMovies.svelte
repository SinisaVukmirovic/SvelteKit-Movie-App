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