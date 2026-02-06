<script>
    import { goto } from "$app/navigation";
    let search = "";
    const breeds = ["Dachshund", "Bulldog", "Poodle", "German Shepherd"];

    function pesquisar() {
        const valor = search.trim().toLowerCase();
        if (!valor) return;

        goto(`/searchpage/${valor}`);
    }
</script>

<div class="search-bar">
    <header>
        <input
            class="div-input"
            type="text"
            placeholder="Pesquise uma raça de cachorro"
            bind:value={search}
        />
        <button
            type="button"
            class="search-button"
            aria-label="Pesquisar raça de cachorro"
            on:click={pesquisar}
        >
            <svg
                xmlns="http://www.w3.org/2000/svg"
                width="100"
                height="100"
                viewBox="0 0 72 72"
            >
                <path
                    d="M 31 11 C 19.973 11 11 19.973 11 31 C 11 42.027 19.973 51 31 51 C 34.974166 51 38.672385 49.821569 41.789062 47.814453 L 54.726562 60.751953 C 56.390563 62.415953 59.088953 62.415953 60.751953 60.751953 C 62.415953 59.087953 62.415953 56.390563 60.751953 54.726562 L 47.814453 41.789062 C 49.821569 38.672385 51 34.974166 51 31 C 51 19.973 42.027 11 31 11 z M 31 19 C 37.616 19 43 24.384 43 31 C 43 37.616 37.616 43 31 43 C 24.384 43 19 37.616 19 31 C 19 24.384 24.384 19 31 19 z"
                ></path>
            </svg></button
        >
    </header>

    <div class="suggestion">
        {#each breeds as breed}
            <button
                type="button"
                class="item"
                on:mousedown={() => (search = breed)}
            >
                {breed}
            </button>
        {/each}
    </div>
</div>

<style>
    .search-bar {
        position: relative;
        width: 600px;
        box-sizing: border-box;
        z-index: 999;
    }
    .search-button svg {
        min-height: 60%;
        min-width: 60%;
        opacity: 50%;
    }
    .search-button {
        all: unset;
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
        width: 40px;
        height: 40px;
    }

    header {
        display: flex;
        align-items: center;
        transition: box-shadow 0.1s linear;
        padding: 10px;
        padding-left: 15px;
        border-radius: 24px;
        height: 50px;
        width: 100%;
        font-size: 15px;
        background-color: #fff;
        border: 1px solid #dfe1e5;
        transition: box-shadow 0.1s linear;
        box-sizing: border-box;
    }
    .div-input {
        border: none;
        height: 100%;
        width: 100%;
    }
    .search-bar svg {
        width: 10%;
    }
    .div-input:focus {
        outline: none;
    }
    header:has(.div-input:hover),
    header:has(.div-input:focus) {
        background-color: #fff;
        box-shadow: 0 1px 6px rgba(32, 33, 36, 0.28);
        border-color: rgba(223, 225, 229, 0);
    }
    header:has(.div-input:focus) {
        border-radius: 24px 24px 0 0;
    }

    .suggestion {
        position: absolute;
        top: calc(100% - 1px);
        left: 0;
        width: 100%;
        height: fit-content;
        display: none;
        background: #fff;
        box-shadow: 0 1px 6px rgba(32, 33, 36, 0.28);
        border-radius: 0 0 16px 16px;
        font-family: Arial, Helvetica, sans-serif;
        z-index: 999;
    }
    .search-bar:has(.div-input:focus) .suggestion {
        z-index: 999;
        display: flex;
        flex-direction: column;
        padding-top: 10px;
        padding-bottom: 10px;
        gap: 8px;
    }
    .suggestion .item {
        width: fit-content;
        background: none;
        border: none;
        padding: 10px 15px;
        cursor: pointer;
        font-size: 14px;
    }
</style>
