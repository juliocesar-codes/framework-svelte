<script>
    import Input from "../components/+input.svelte";
    import Card from '../components/+card.svelte';


    import doogleImg from "../public/Doogle.png"
    
</script>

<main>
    <img src={doogleImg} alt="Doogle"/>
    <Input/>
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
        gap: 5%;
    }
    img {
        height: fit-content;
    }
</style>