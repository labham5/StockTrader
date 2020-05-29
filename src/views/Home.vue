<template>
  <div class="home">
    <b-container>
      
      <h1>
        Trade or view your portfolio
      </h1>
      <h3>
        You may save/Load your data
      </h3>
      <h6>
        Click on 'End Day' to begin a New Day
      </h6>
      <br>
      <p>
        Your fund: {{funds}}
      </p>
    </b-container>
    
  </div>
</template>

<script>

export default {
  name: 'Home',
  components: {

  },
  computed:{
    funds(){
      return this.$store.getters.funds;
    }
  }
}
</script>
