<script>
import Game from './components/Game.vue'

export default {
        components: {
          Game
        }
    };


</script>

<template>
 
  <div class="flex flex-col justify-start items-center min-h-screen bg-blue-100 pt-6">

    <h1 class="font-bold text-4xl">Rock Paper Scissors Game</h1>

    <div class="mt-8 border-4 border-black p-4">
      <game />
    </div>

  </div>

</template>