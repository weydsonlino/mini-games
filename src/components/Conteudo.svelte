<script lang="ts">

    class post {
        public postTittle: string;
        public postContent: string;
        public postImage: string;
        public postImageAlt: string;
        public rota:string;

        constructor(postTittle:string, postContent:string, postImage:string, postImageAlt:string, rota:string) {
            this.postTittle = postTittle;
            this.postContent = postContent;
            this.postImage = postImage;
            this.postImageAlt = postImageAlt;
            this.rota = rota;

        }
    }

    const posts = [
        new post('Adivinha??', 'Adivinha é um jogo onde você tem que descobrir a que pessoa ou personagem o game está se referindo.', 'https://i.ibb.co/3dhDRVv/adivinha.png', 'Imagem do game Adivinha?', '/Adivinha'),
        new post('Jogo da memoria', 'Jogo da memoria é um jogo da memoria (kkkk) com alguns personagens do LoL, um jogo que eu não pretendo continuar-lo agora', 'https://i.ibb.co/TRZZ40v/Captura-de-tela-2024-03-29-203454.png','Imagem do game Jogo da memoria','https://memory-game-59soty7rb-weydsonlino.vercel.app/')
    ]

</script>

<main id="espacoConteudo">
    <h1 id="tittleArea">Mini Games</h1>

    <div id="postsArea"> 
        {#each posts as post}
        <div class="post">
            <h2 class="postTittle">{post.postTittle}</h2>
            <p class="postContent">{post.postContent}</p>
            <img class="postImage" src="{post.postImage}" alt="{post.postImageAlt}" srcset="{post.postImage}">
            <button class="postButton" type="button"><a href="{post.rota}">Jogar</a></button>
        </div>
        {/each}

        
    </div>
</main>


<style>
    #espacoConteudo{
        
    }
    
    #tittleArea{
        text-align: center;
    }
    #postsArea{
        display: flex;
        margin-top: 50px;
    }
    .post{
        margin: 20px;
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 420px;
        width: 275px;
        background-color: #ffb200;
        padding: 10px;
        border-radius: 2%;
    }
    .postTittle{
        font-size: 25px;
        margin: 5px;
    }
    .postContent{
        text-align: center;
    }
    .postImage{
        width: 250px;
        height: 250px;
    }
    .postButton{
        justify-self: flex-end;
        margin: 10px;
        width: 70px;
    }


</style>