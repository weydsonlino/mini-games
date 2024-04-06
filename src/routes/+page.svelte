<script lang="ts">
    import Conteudo from "../lib/components/Conteudo.svelte";
    import Footer from "../lib/components/footer.svelte";
    import NavBAr from "../lib/components/NavBAr.svelte";

</script>
<body id="inicioBody">
    <NavBAr link = "\Adivinha" text = "Jogar"/>
    <h1 id="tilte">Mini Games</h1>
    <div id="content">
    <Conteudo/>
        </div>
    <Footer/>   
</body>

<style>
    #inicioBody{
        display: flex;
        flex-direction: column;
        height: 100vh;
    }
    #tilte{
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 75px;
        margin-top: 20px;
    }
    #content{
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }
    
</style>