<template>
  <div class="games">
    <div class="container">
      <GameCard />
    </div>
  </div>
</template>

<script>
  import GameCard from '@/components/GameCard.vue'

  export default {
    name: 'Games',
    components: {
      GameCard
    },
  }
</script>