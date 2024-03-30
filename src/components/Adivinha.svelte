<script lang="ts">

//Estabelecendo variaveis para controle do game
    let desafioAtual = 0
    let respostaUser = ""
    let controle = ""
    let status =""
    let dicas = 0
    let pontos = 0
    let pontoDesafios = 100
    const quantidadeDicas = 2
    const evitarRepeticao = []

    const getHighScore = JSON.parse(localStorage.getItem('Recorde') || "null")
    const score = {
        highScore: 0,
    }
//Criando o LocalStorage
    criandoLocalStorage()
    function criandoLocalStorage(){
        //Pegando o valor do Highscore no local storage (Serve para a checagem da existencia de um localstorage )
        getHighScore
        //Setando o valor do Higscore no jogo com o valor do storagelocal
        score.highScore = getHighScore
        //Chegando se existe algum recorde no storage
        if (getHighScore > 0) {
            //Sicnoizando o recorde do game com o pre guardado no local storage
            score.highScore = getHighScore
        }else{
            //Setando o highscore para 0 se não o resultado sera "null"
            score.highScore = 0
            //Criando o local storage já q não existe um ainda
            const setHighScore = localStorage.setItem('Recorde', JSON.stringify(score.highScore))
            getHighScore
            
        }

    }

//Criando um "objeto" dos desafios e atribuindo caracteristica a eles
    class desafios{
        public tema: string;
        public dica1: string;
        public dica2: string;
        public dica3: string;
        public resposta: string;
        public pontuacao: number;
        constructor(tema:string, dica1:string, dica2:string, dica3:string, resposta:string, pontuacao:number){
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
        new desafios('League of legends','Sou verde', 'Sou o monstro de baixo da sua cama', 'Capturo mulheres', 'tresh', pontoDesafios),
        new desafios('Personagem de filme', 'Tenho rodas', 'Eu corro na copa pistão', 'Prefiro ajudar um amigo do que vencer', 'relampago mcqueen', pontoDesafios),
        new desafios('Valorant','Sou roxa','Quando ulto fico encapetada', 'Gosto de almas', 'reyna', pontoDesafios),
        new desafios('Overwatch', 'Sou uma garota', 'Pede pra nerfar', 'Eu tenho algo que me ajuda a voar', 'd.va', pontoDesafios),
        new desafios('League of Legends', 'Sou de Demacia', 'Enquando eu puder me levantar eu lutarei', 'Minha espada é gigante', 'garen', pontoDesafios),
        new desafios('Personagem de filme', 'Moro distante de todos', 'Sou verde', 'Tenho um amigo burro', 'shrek', pontoDesafios),
        new desafios('Personagem de filme', 'Sou uma princesa', 'Tenho poderes','Deixo tudo congelado', 'elsa', pontoDesafios),
        new desafios('Valorant', 'Gosto das minhas bombas', 'Eu explodo tudo', 'Sou Bahiana', 'raze', pontoDesafios),
    ]
    
    aleatorizarDesafios()
    controle = todosDesafios[desafioAtual].resposta
    function aleatorizarDesafios(){

        const numMin = Math.ceil(0);
        const numMax = Math.floor(todosDesafios.length);
        desafioAtual =  Math.floor(Math.random() * (numMax - numMin)) + numMin;
        
        if (todosDesafios.length == evitarRepeticao.length ) {
            status = "Acabou"
        }else if(evitarRepeticao.length < todosDesafios.length){
            
            while (evitarRepeticao.includes(desafioAtual)) {
                const numMin = Math.ceil(0);
                const numMax = Math.floor(todosDesafios.length);
                desafioAtual =  Math.floor(Math.random() * (numMax - numMin)) + numMin;
            }
            evitarRepeticao.push(desafioAtual)
        }
        
        
        console.log("Evitar = ", evitarRepeticao);
        console.log("Evitar tamanho = ", evitarRepeticao.length)
        console.log("Desafios = ",todosDesafios.length)
        

    }
    
//Funções
    function pedirDica() {
        if (dicas <= quantidadeDicas) {
            dicas ++
            todosDesafios[desafioAtual].pontuacao -= 20
        } 
    }
    function conferirResposta(){
        criandoLocalStorage() 

        respostaUser = respostaUser.toLocaleLowerCase()
        if (respostaUser == controle) {
            status = "Acertou"
            setTimeout(reiniciarJogo, 2000)
            pontos += todosDesafios[desafioAtual].pontuacao
            saveHighScore()
        }
        else if(respostaUser ==""){
            status = "Escreva algo"
            setTimeout(resetarStatus, 2000)
        }
        else{
            todosDesafios[desafioAtual].pontuacao -= 10
            status = "Errou"
            setTimeout(resetarStatus, 2000)
        }
    }

    function saveHighScore(){
        if (pontos > getHighScore) {
            score.highScore = pontos
            const setHighScore = localStorage.setItem('Recorde', JSON.stringify(score.highScore))
        }
    }

    function resetarStatus() {
        respostaUser = ""
        status = ""
    }
    function reiniciarJogo() {
        status = ""
        aleatorizarDesafios()
        saveHighScore()
        
        respostaUser = ""
        controle = todosDesafios[desafioAtual].resposta
        dicas = 0
    }

</script>

<main id="conteiner">

    

    <h1 id="jogoSelecionado">Adivinha?¿</h1>
    

    <div id="jogo">
        <h2 id="tittle">{todosDesafios[desafioAtual].tema}</h2>
        <div id="espacoPontuacao">
            <h2 class="pontuacao">Pontuação: {pontos}</h2>
            <h2 class="pontuacao">Record: {score.highScore}</h2>
        </div>
        

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
                    <button on:click={reiniciarJogo} class="button-35" >Pular desafio</button>
                {/if}

                {#if status == "Acabou"}
                    <button class="button-35" >Enviar</button>
                {:else}
                    <button on:click={conferirResposta} class="button-35" >Enviar</button>
                {/if}
                
            </div>
            <div id="espacoStatus">
                {#if respostaUser == controle}
                    <p id="statusAcerto">{status}</p>
                {:else if !(status == "")}
                    <p id="statusErro">{status}</p>
                {/if}
            </div> 
        </div>    
    </div>
</main>










<style>
    #jogoSelecionado{
        align-self: center;
        color:#ffffff;
        font-weight: bolder;
    }
    #conteiner{
        display: flex;
        flex-direction: column;
        font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    }
    #jogo{
        height: 470px;
        width: 350px;
        background-color: #f0d01a;
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
        color: #df7c0a;;
        font-size: 30px;
        text-decoration: underline;
        font-weight: bolder;
        margin: 10px 0 0px 0;
    }
    #espacoPontuacao{
        display: flex;
        justify-content: space-around;
    }
    .pontuacao{
        font-size: 20px;
        font-weight: normal;
    }
    #espacoDescricao{
        height: 200px;
    }
    .descricao{
        margin-bottom: 30px;
        font-size: 20px;
        margin-left: 10px;
    }
    #EspacoBotoes{
        display: flex;
    }
    #EspacoUsuario{
        display: flex;
        flex-direction: column;
        justify-content: flex-end;
    }
    #espacoStatus{
        height: 50px;
        align-self: center;
        font-size: 20px;
    }
    #statusAcerto{
        background-color: green;
    }
    #statusErro{
        background-color: red;
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
    
</style>


