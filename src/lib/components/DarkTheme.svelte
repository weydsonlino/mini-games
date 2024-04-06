<script lang="ts">
    import { toggleMode } from "mode-watcher";
  </script>
   
  <button on:click={toggleMode}>

    <img src="https://i.pinimg.com/564x/d8/dc/3a/d8dc3a2fd41076ec9e52eea65ac62da0.jpg" alt="AA" class="absolute h-[1.2rem] w-[1.2rem] rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100"
    />
    <img src="www.google.com" alt="AA" class="absolute h-[1.2rem] w-[1.2rem] rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100"
    />
    <span class="sr-only">Toggle theme</span>

  </button>