<script>
  import Adivinha from "../../components/Adivinha.svelte";
  import NavBAr from "../../components/NavBAr.svelte";



</script>
    <body>
        <NavBAr/>   
        <main id="campoJogo">
            <Adivinha/>
            <button><a href="/">Inicio</a></button>
        </main>
    </body>
    

<style>
    #campoJogo{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }
</style>