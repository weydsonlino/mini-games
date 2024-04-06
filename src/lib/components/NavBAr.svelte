<script lang="ts">
    export let link:string;
    export let text:string;

</script>

<div class="div">
    <h1 id="groupName">WS DEVELOPERS</h1>
    <a href="{link}"><div class="navButton">{text}</div></a>
  </div>
  <style>
    .div {
      background-color: #fff;
      display: flex;
      gap: 20px;
      font-size: 32px;
      font-weight: 400;
      padding: 25px 79px;
    }
    @media (max-width: 991px) {
      .div {
        flex-wrap: wrap;
        padding: 0 20px;
      }
    }
    #groupName {
      color: #000;
      font-family: Cutive Mono;
      font-size: 32px;
      flex-grow: 1;
      flex-basis: auto;
      margin: auto 0;
      margin: 0;
    padding: 0;
    border: 0;
    font-size: 100%;
    font: inherit;
    vertical-align: baseline;
    }
    .navButton {
      font-family: Inter, sans-serif;
      justify-content: center;
      border-radius: 2px;
      background-color: #000;
      color: #fff;
      white-space: nowrap;
      padding: 17px 32px 10px;
      font-size: 17px;
    }
    @media (max-width: 991px) {
      .navButton {
        white-space: initial;
        padding: 0 20px;
      }
    }
  </style>
  