<script>
//Estabelecendo variaveis para controle do game
    let desafioAtual = 0
    let respostaUser = ""
    let controle = ""
    let status = ""
    let dicas = 0
    let pontos = 0
    const quantidadeDicas = 2

//Criando um "objeto" dos desafios e atribuindo caracteristica a eles
    class desafios{
        constructor(tema, dica1, dica2, dica3, resposta, pontuacao){
        this.tema = tema
        this.dica1 = dica1
        this.dica2 = dica2
        this.dica3 = dica3
        this.pontuacao = pontuacao
        this.resposta = resposta
        }
    }

//Criando os desafios de forma individual de acordo com as caracteristica da class
    const todosDesafios = [
        new desafios('League of legends','Sou verde', 'Sou o monstro de baixo da sua cama', 'Capturo mulheres', 'tresh', 100),
        new desafios('Personagem de filme', 'Tenho rodas', 'Eu corro na copa pistão', 'prefiro ajudar um amigo do que vencer', 'relampago mcqueen', 100),
        new desafios('Valorant','Sou roxa','Quando ulto fico encapetada', 'Gosto de almas', 'reyna', 100),
        new desafios('Overwatch', 'Sou uma garota', 'Pede pra nerfar', 'Eu tenho algo que me ajuda a voar', 'd.va', 100)
    ]
    controle = todosDesafios[desafioAtual].resposta
    
//Funções
    function pedirDica() {
        if (dicas <= quantidadeDicas) {
            dicas ++
            todosDesafios[desafioAtual].pontuacao -= 20
        } 
    }
    function conferirResposta(){

        respostaUser = respostaUser.toLocaleLowerCase()
        if (respostaUser == controle) {
            status = "Acertou"
            setTimeout(reiniciarJogo, 3000)
            pontos += todosDesafios[desafioAtual].pontuacao

        }
        else{
            todosDesafios[desafioAtual].pontuacao -= 10
            status = "Errou"
        }
    }
    function reiniciarJogo() {
        if (desafioAtual >= (todosDesafios.length - 1)) {
            desafioAtual = 0
        }
        else{
            desafioAtual++
        }
        status = ""
        respostaUser = ""
        controle = todosDesafios[desafioAtual].resposta
        console.log(controle)
        dicas = 0
    }

</script>

<main id="conteiner">

    <h1 id="jogoSelecionado">Adivinha?¿</h1>


    <div id="jogo">
        
        <h2 id="tittle">{todosDesafios[desafioAtual].tema}</h2>

        <div id="espacoDescricao">
            <p class="descricao">{todosDesafios[desafioAtual].dica1}</p>
            {#if dicas >= 1}
                <p class="descricao">{todosDesafios[desafioAtual].dica2}</p>
            {/if}
            {#if dicas >= 2}
                <p class="descricao">{todosDesafios[desafioAtual].dica3}</p>
            {/if}
        </div>
        
        <div id="EspacoUsuario">
            <input type="text" id="respostaUser" placeholder="Resposta"bind:value={respostaUser}/>
            <div id="EspacoBotoes">
                {#if dicas < quantidadeDicas}
                    <button on:click={pedirDica} class="button-35">Dica {dicas}/{quantidadeDicas}</button>
                {:else}
                    <button on:click={pedirDica} class="button-35" disabled >Não tem mais dicas</button>
                {/if}
                
                <button on:click={conferirResposta} class="button-35" >Enviar</button>
            </div>
                <p id="status">{pontos} <br> {status}</p>
        </div>    
    </div>
</main>










<style>
    #jogoSelecionado{
        align-self: center;
        color:rgb(54, 166, 170);
    }
    #conteiner{
        display: flex;
        flex-direction: column;
    }
    #jogo{
        height: 450px;
        width: 350px;
        background-color: rgb(54, 166, 170);
        padding: 30px;
        display: flex;
        flex-direction: column;
        border-radius: 5%;
        font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        border: ridge;
        border-color: #121212;
    }
    #tittle{
        align-self: center;
        font-family: 'Courier New', Courier, monospace;
    }
    #espacoDescricao{
        height: 200px;
    }
    .descricao{
        margin-bottom: 30px;
        font-size: 20px;
        font-weight: bold;
    }
    #EspacoBotoes{
        display: flex;
    }
    #EspacoUsuario{
        display: flex;
        flex-direction: column;
        justify-content: flex-end;
    }
    #respostaUser{
        margin: 10px 0px 10px 0px;
        width: 250px;
        align-self: center;
        border: 0;
        outline: 0;
        color: rgb(60, 66, 87);
        background-color: rgb(255, 255, 255);
        box-shadow: rgb(0 0 0 / 0%) 0px 0px 0px 0px, rgb(0 0 0 / 0%) 0px 0px 0px 0px, rgb(0 0 0 / 0%) 0px 0px 0px 0px, rgb(60 66 87 / 16%) 0px 0px 0px 1px, rgb(0 0 0 / 0%) 0px 0px 0px 0px, rgb(0 0 0 / 0%) 0px 0px 0px 0px, rgb(0 0 0 / 0%) 0px 0px 0px 0px;
        border-radius: 4px;
        font-size: 14px;
        line-height: 20px;
        font-weight: 400;
        padding: 4px 8px;
        min-height: 28px;
        vertical-align: middle;
        transition: background-color .24s,box-shadow .24s;
        transition-property: background-color, box-shadow;
        transition-duration: 0.24s, 0.24s;
        transition-timing-function: ease, ease;
        transition-delay: 0s, 0s;          
    }
    #respostaUser:focus{
        box-shadow: rgb(0 0 0 / 0%) 0px 0px 0px 0px, rgb(58 151 212 / 36%) 0px 0px 0px 4px, rgb(0 0 0 / 0%) 0px 0px 0px 0px, rgb(60 66 87 / 16%) 0px 0px 0px 1px, rgb(0 0 0 / 0%) 0px 0px 0px 0px, rgb(0 0 0 / 0%) 0px 0px 0px 0px, rgb(0 0 0 / 0%) 0px 0px 0px 0px;
    }
    .button-35 {
        align-self: center;
        width: 75px;
        align-items: center;
        background-color: #fff;
        border-radius: 12px;
        box-shadow: transparent 0 0 0 3px,rgba(18, 18, 18, .1) 0 6px 20px;
        box-sizing: border-box;
        color: #121212;
        cursor: pointer;
        display: inline-flex;
        flex: 1 1 auto;
        font-family: Inter,sans-serif;
        font-size: 15px;
        font-weight: 700;
        justify-content: center;
        line-height: 1;
        margin: 10px 15px;
        outline: none;
        padding: 1rem 1.2rem;
        text-align: center;
        text-decoration: none;
        transition: box-shadow .2s,-webkit-box-shadow .2s;
        white-space: nowrap;
        border: 0;
        user-select: none;
        -webkit-user-select: none;
        touch-action: manipulation;
    }

    .button-35:hover {
        box-shadow: #121212 0 0 0 3px, transparent 0 0 0 0;
    }
    #status{
        align-self: center;
        font-size: 20px;
    }
</style>


