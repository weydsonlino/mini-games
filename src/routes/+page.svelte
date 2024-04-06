<script lang="ts">
    import Conteudo from "../lib/components/Conteudo.svelte";
    import Footer from "../lib/components/footer.svelte";
    import { ModeWatcher } from "mode-watcher";

</script>
<body id="inicioBody">
    
    <div id="content">
        <Conteudo/>
    </div>
    <Footer/>   
</body>

<style>
    #inicioBody{
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: center;
        width: 96vw;
        height: 90vh;
        background-color: #df7c0a;
        font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    }
    #content{
        display: flex;
        flex-direction: row;
    }
    
</style>