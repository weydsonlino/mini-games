<script>
    
    const navItens = ["Jogo", "Testes"]

</script>

<nav id="nav">

    <a href="/" class="navItens">Inicio</a>
    {#each navItens as Item }
        
    <a href="/{Item}" class="navItens">

        {Item}
    </a>

    {/each}

    
</nav>




<style>
    #nav{
        display: flex;
        flex-direction: column;
        width: 150px;
        height: 100vh;
        background-color: aqua;
    }
    .navItens{
        color: rgb(38, 36, 155);
        font-size: 50px;
        text-decoration: none;
        margin: 10px;
        width: 75px;
    }

</style>