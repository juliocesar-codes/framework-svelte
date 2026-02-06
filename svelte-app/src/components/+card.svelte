<script>
  export let src

</script>

<div class="card">
  <img src={src} alt="Dog"/>
</div>

<style>
  .card {
    height: 250px;
    max-height: 1000px;
    border-radius: 20px;
    overflow: hidden;
    display: flex;
    flex-grow: 1;
    background: rgba(255, 255, 255, 0.2);
    border-radius: 16px;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(8px);
    border: 1px solid rgba(255, 255, 255, 0.3);
    transition:
      transform 0.3s ease,
      box-shadow 0.3s ease;
    font-family: sans-serif;
    
  }
  .card img{
    width: 100%;
    height: 100%;

    object-fit: cover;
    transition: 1s ease;
    filter: brightness(0.8);
  }
  .card img:hover{
    filter: brightness(1);
  }
  .card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 40px rgba(0, 0, 0, 0.15);
    
  }
</style>
