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
        dogsApiImageResponse = data.message;
    });
</script>

<header>
    <img src={doogleImg} alt="" />
    <Input />
</header>
<main>
    <div class="container-photos">
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
        flex-wrap: wrap;
        gap: 2rem;
        padding: 30px;
        padding-top: 100px;
        box-sizing: border-box;
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
</style>
