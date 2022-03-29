<!-- to do a Server Side Rendered fetch request we use script with context="module" -->
<script context="module">
    // !!! can't get environment variables to work !!!
    // import { MY_API_KEY } from '$lib/Env';
    // console.log(MY_API_KEY);

    export async function load({ fetch }) {
        const apiUrl = `https://api.themoviedb.org/3/movie/popular?api_key=6022a4ae03ca3a0275414b787f65b604`;
        // const apiUrl = `https://api.themoviedb.org/3/movie/popular?api_key=${MY_API_KEY}`;
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
    import SearchMovies from '../components/SearchMovies.svelte';
    import PopularMovies from '../components/PopularMovies.svelte';
    import { fly } from 'svelte/transition';

    export let popular;
</script>

<section in:fly={{y: 100, duration: 500}}
         out:fly={{ duration: 500 }}>
    <SearchMovies />

    <PopularMovies {popular} />
</section>