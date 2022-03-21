<form class="search">
    <label for="search_movie">Search Movie:</label>
    <input name="search_movie" type="text" />
    <button>Search</button>
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
        padding: .5rem 0;
        transition: background .7s ease-out;
        font-weight: bold;
        background-color: rgb(63, 63, 63);
        border-radius: .7rem;
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