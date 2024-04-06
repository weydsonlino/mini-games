<script lang="ts">
    export let postTittle:string;
    export let postImage:string;
    export let postContent:string;
    export let postImageAlt:string;
    export let postLink:string;
</script>

  <div class="column">
    <div class="div-5">
      <div class="div-6">{postTittle}</div>
      <img
        loading="lazy"
        srcset="{postImage}"
        class="img"
        alt="{postImageAlt}"
      />
      <div class="div-7">{postContent}</div>
      <div class="div-8"><a href="{postLink}" class="div-8">Jogar</a></div>
    </div>
  </div>
  <style>
    .column {
      display: flex;
      flex-direction: column;
      line-height: normal;
      width: 20%;
      margin-left: 25px;
      margin-right: 50px;
    }
    @media (max-width: 991px) {
      .column {
        width: 100%;
      }
    }
    .div-5 {
      border-radius: 12px;
      background-color: #000;
      display: flex;
      flex-grow: 1;
      flex-direction: column;
      color: #fff;
      font-weight: 400;
      width: 100%;
      padding: 18px 29px;
    }
    @media (max-width: 991px) {
      .div-5 {
        margin-top: 40px;
        padding: 0 20px;
      }
    }
    .div-6 {
      align-self: center;
      font: 32px Inter, sans-serif;
    }
    .img {
      aspect-ratio: 0.98;
      object-fit: auto;
      object-position: center;
      width: 100%;
      margin-top: 24px;
    }
    .div-7 {
      margin-top: 11px;
      font: 15px Inter, sans-serif;
    }
    .div-8 {
      justify-content: center;
      border-radius: 2px;
      background-color: #fff;
      align-self: end;
      margin-top: 50px;
      color: #000;
      white-space: nowrap;
      padding: 10px 14px;
      font: 24px Inter, sans-serif;
      text-decoration: none;
    }
    @media (max-width: 991px) {
      .div-8 {
        margin-top: 40px;
        white-space: initial;
      }
    }
  </style>
  