<script context="module">
    export async function load({ fetch, params }) {
        const apiUrl = `https://api.themoviedb.org/3/search/movie?api_key=6022a4ae03ca3a0275414b787f65b604&language=en-US&query=${params.id}&page=1&include_adult=false`;
        const res = await fetch(apiUrl);
        const data = await res.json();

        if (res.ok) {
            return {
                props: { searchedMovie: data.results }
            }
        }
    }
</script>

<script>
    import MovieCard from "../../components/MovieCard.svelte";
    export let searchedMovie;
</script>

<div class="searched-movies">
    {#each  searchedMovie as movie}
        <MovieCard {movie} />
    {/each}
</div>

<style>
    .searched-movies {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
        grid-gap: 1rem .5rem;
    }
</style>