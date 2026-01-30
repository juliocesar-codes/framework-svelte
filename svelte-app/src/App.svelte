<script>
    import Input from "./components/input.svelte";

    const raca = "bulldog"

    import { onMount } from "svelte";

    const endpoint = `https://dog.ceo/api/breed/${raca}/images`;

    let data = [];

    onMount(async function () {
        const response = await fetch(endpoint);
        const data = await response.json();
        console.log(data);
    });

    
</script>

<main>
    <img src="https://i.ibb.co/w1MYVvb/Doogle.png" alt="Doogle" border="0" />
    <Input />
</main>

<style>
    main {
        background-color: f0f0f0;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 100%;
        width: 100%;
        gap: 20px;
    }
    img {
        height: fit-content;
    }
</style>