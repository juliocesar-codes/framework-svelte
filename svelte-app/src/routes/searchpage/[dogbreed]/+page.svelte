<script>
    import Input from "../../../components/+input.svelte";
    import Card from "../../../components/+card.svelte";

    import doogleImg from "../../../public/Doogle.png";

    /** @type {{ data: import('./$types').PageData }} */
    let { data } = $props();
    import { onMount } from "svelte";
    const endpoint = `https://dog.ceo/api/breed/${data.post.dogBreed}/images`;

    let dogsApiImageResponse = $state([]);

    onMount(async function () {
        const response = await fetch(endpoint);
        const data = await response.json();

        if (data.status == "error") dogsApiImageResponse = [];
        else dogsApiImageResponse = data.message;
    });

    $effect(async () => {
        const breed = data.post.dogBreed;
        if (!breed) return;

        const response = await fetch(
            `https://dog.ceo/api/breed/${breed}/images`,
        );
        const json = await response.json();
        if (json.status == "error") {
            dogsApiImageResponse = [];
        } else {
            dogsApiImageResponse = json.message;
        }
    });
</script>

<header>
    <a href="http://localhost:5173/">
        <img src={doogleImg} alt="dog" />
    </a>
    <Input />
</header>
<main>
    <div class="container-photos">
        {#if dogsApiImageResponse.length == 0}
            <p>Error 404: Raça não encontrada</p>
        {/if}
        {#each dogsApiImageResponse as dogImage}
            <Card src={dogImage} />
        {/each}
    </div>
</main>

<style>
    header {
        position: fixed;
        z-index: 999;
        display: flex;
        height: 10%;
        width: 100%;
        align-items: center;
        padding-left: 40px;
        gap: 40px;
        outline: 1px solid #00000022;
        background-color: white;
    }
    header img {
        max-height: 30px;
    }

    main {
        display: flex;
        gap: 2rem;
        padding: 30px;
        padding-top: 100px;
        box-sizing: border-box;
    }
    main p{
        font-size: 20px;
    }
    .container-photos {
        display: flex;
        flex-wrap: wrap;
        flex-grow: 1;
        gap: 10px;
        gap: 2rem;
        padding: 30px;
        box-sizing: border-box;
    }
    .img-error{
        height: 550px;
    }
</style>
