<script>
    import Adivinha from "../../components/Adivinha.svelte";
    import NavBAr from "../../components/NavBAr.svelte";
  import Footer from "../../components/footer.svelte";
  
</script>
    <body id="bodyJogo">
            <NavBAr/>   
        <main id="campoJogo">
            <Adivinha/>
        </main>
        <Footer/>
    </body>
    

<style>
    #bodyJogo{
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 100vh;
    }
    #campoJogo{
        display: flex;
        flex-direction: column;
        align-items: center;
        
    }
</style>