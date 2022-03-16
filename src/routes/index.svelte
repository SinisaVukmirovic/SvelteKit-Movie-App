<!-- to do a Server Side Rendered fetch request we use script with context="module" -->
<script context="module">
    export async function load({ fetch }) {
        const apiUrl = 'https://api.themoviedb.org/3/movie/popular?api_key=6022a4ae03ca3a0275414b787f65b604';
        const res = await fetch(apiUrl);
        const data = await res.json();

        if (res.ok) {
            return {
                props: { popular: data.results }
            }
        }
    }
</script> 

<script>
    import PopularMovies from '../components/PopularMovies.svelte';
    export let popular;
    console.log(popular)
</script>

<section>
    <PopularMovies {popular} />
</section>