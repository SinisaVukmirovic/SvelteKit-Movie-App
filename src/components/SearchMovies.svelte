<script>
    import { goto } from '$app/navigation';
    import { fly } from 'svelte/transition';

    let inputValue = '';
    let active = false;
    let cancelInactive = () => {
        if (inputValue) {
            active = true;
        } else {
            active = false;
        }
    }

    function submitSearch() {
         goto(`/search/${inputValue}`);
    }
</script>

<form class="search" on:submit|preventDefault={submitSearch}>
    {#if !active }
        <label for="search_movie"
            in:fly={{ y: -10, duration: 500 }}
            out:fly={{ y: -10, duration: 500 }}>Search Movie:
        </label>
    {/if}
    <input bind:value={inputValue} 
        on:focus={() => active = true}
        on:blur={cancelInactive} 
        name="search_movie" type="text"
        class={active ? 'selected' : ''} />

    {#if inputValue}    
        <button in:fly={{ x: 20, duration: 500 }}
                out:fly={{ x: 20, duration: 500 }}>Search</button>
    {/if}
</form>

<style>
    .search {
        position: relative;
        width: 50%;
        margin: 1rem;
    }
    button {
        font-size: .7rem;
        padding: 0 1rem;
        background-color: rgb(96, 110, 201);
        color: #fff;
        font-weight: bold;
        border: none;
        position: absolute;
        bottom: 50%;
        right: 0;
        transform: translateY(50%);
        height: 100%;
        border-top-right-radius: .7rem;
        border-bottom-right-radius: .7rem;
        cursor: pointer;
    }

    input {
        width: 100%;
        border: none;
        outline: none;
        font-size: 1rem;
        font-family: 'Poppins', sans-serif;
        color: rgb(255, 255, 255);
        padding: .5rem;
        transition: background .7s ease-out;
        font-weight: bold;
        background-color: rgb(63, 63, 63);
        border-radius: .7rem;
    }
        input.selected {
            background-color: rgb(10, 10, 10);
        }

    label {
        position: absolute;
        font-size: .8rem;
        top: 50%;
        left: 0;
        transform: translateY(-50%);
        pointer-events: none;
        color: #fff;
        padding: 0 1rem;
    }
</style>