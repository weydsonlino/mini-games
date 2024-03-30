<script>
    
    const navItens = ["Adivinha"]

</script>

<nav >
    <ul id="nav">
        <li  class="navItens"><a href="/">Inicio</a></li>
        {#each navItens as Item }
            
       <li  class="navItens"><a href="/{Item}">

            {Item}
        </a></li>
        {/each}

        <li class="navItens"><a href="https://memory-game-59soty7rb-weydsonlino.vercel.app/">Jogos Antigos</a></li>
    </ul>

</nav>




<style>
    #nav{
        display: flex;
        flex-direction: row;
        justify-content: center;
        width: 100vw;
        margin-bottom: 0px;
        background-color: wheat;
    }
    .navItens{
        font-size: 25px;
        text-decoration: none;
        margin: 10px;
        width: 200px;
        list-style: none;
        text-decoration: none ;
    }
    a{
        text-decoration: none;
        color: black;
    }
    

</style>