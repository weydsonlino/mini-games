<script>
    import Adivinha from "../../components/Adivinha.svelte";
    import NavBAr from "../../components/NavBAr.svelte";
  
</script>
    <body id="bodyJogo">

            <NavBAr/>   
        <main id="campoJogo">
            <Adivinha/>
        </main>
    </body>
    

<style>
    #bodyJogo{
        display: flex;
    }
    #campoJogo{
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 100vh;
        margin-left: 450px;
    }
</style>