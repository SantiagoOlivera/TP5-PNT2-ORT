<template >
  <section class="src-components-header-rgb-color">
    <div 
      class="background color-white height " 
      :style="{ background: ganaIn ? `rgb(${colorIn.r},${colorIn.g},${colorIn.b})` : 'steelblue' }">
      <h2>THE GREAT</h2>
      <h1>RGB ( {{colorIn.r}} , {{colorIn.g}} , {{colorIn.b}}) </h1>
      <h2>GUESSING GAME</h2>
    </div>
  </section>
</template>

<script >

  export default  {
    name: 'src-components-header-rgb-color',
    props: ['colorIn', 'ganaIn'],
    mounted () {

    },
    data () {
      return {
      }
    },
    methods: {
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  
  h1{
    font-size: 50px;
  }
  .height{
    height: 200px;
  }
  .color-white{
    color: white;
  }
  .background{
    background: steelblue;
  }
  .src-components-header-rgb-color {

  }
</style>
