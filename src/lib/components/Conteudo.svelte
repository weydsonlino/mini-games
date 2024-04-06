<script lang="ts">
  import CardJogos from "./CardJogos.svelte";
  import NavBAr from "./NavBAr.svelte";

  let postAtual:number = 0;

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
      new post('Adivinha?¿', 'Adivinha é um jogo onde você tem que descobrir a que pessoa ou personagem o game está se referindo.', 'https://i.ibb.co/3dhDRVv/adivinha.png', 'Imagem do game Adivinha?', '/Adivinha'),
      new post('Jogo da memoria', 'Jogo da memoria é um jogo da memoria (kkkk) com alguns personagens do LoL, um jogo que eu não pretendo continuar-lo agora', 'https://i.ibb.co/TRZZ40v/Captura-de-tela-2024-03-29-203454.png','Imagem do game Jogo da memoria','https://memory-game-59soty7rb-weydsonlino.vercel.app/'),
  ]

</script>
<div class="div">
  <div class="div-2">Jogos Disponiveis</div>
  <div class="div-3">
    <div class="div-4">
      {#each posts as post}
      <CardJogos postTittle={post.postTittle} postContent={post.postContent} postImage={post.postImage} postImageAlt={post.postImageAlt} postLink={post.rota}/>
      {/each}
    </div>
  </div>
</div>

<style>
  .div {
      display: flex;
      flex-direction: column;
      padding: 0 20px;
    }
    .div-2 {
      color: #000;
      align-self: center;
      font: 300 40px Inter, sans-serif;
    }
    @media (max-width: 991px) {
      .div-2 {
        font-size: 40px;
      }
    }
    .div-3 {
      margin-top: 61px;
      width: 100%;
    }
    @media (max-width: 991px) {
      .div-3 {
        max-width: 100%;
        margin-top: 40px;
      }
    }
    .div-4 {
      gap: 20px;
      display: flex;
      justify-content: center;
    }
    @media (max-width: 991px) {
      .div-4 {
        flex-direction: column;
        align-items: stretch;
        gap: 0px;
      }
    }


</style>