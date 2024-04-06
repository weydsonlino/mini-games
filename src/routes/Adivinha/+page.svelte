<script lang="ts">

    import Adivinha from "../../lib/components/Adivinha.svelte";
    import NavBAr from "../../lib/components/NavBAr.svelte";
    import Footer from "../../lib/components/footer.svelte";
</script>
    <body id="bodyJogo">
        <NavBAr link="/" text="Menu"/>   
        <main id="campoJogo">
            <Adivinha/>
        </main>
        <Footer/>
    </body>
    

<style>
    #bodyJogo{
        display: flex;
        flex-direction: column;
        height: 100vh;
    }
    #campoJogo{
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }
</style>