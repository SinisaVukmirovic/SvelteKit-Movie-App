<script context="module">
    export async function load({ fetch, params }) {
        const apiUrl = `https://api.themoviedb.org/3/search/movie?api_key=6022a4ae03ca3a0275414b787f65b604&language=en-US&query=${params.id}&page=1&include_adult=false`;
        const res = await fetch(apiUrl);
        const data = await res.json();

        console.log(data);

        if (res.ok) {
            return {
                props: { searchedMovie: data.results }
            }
        }
    }
</script> 