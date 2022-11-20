<template >

  <section class="src-components-options">
    <div class="background">
      <div class="flex">
        
        <div class="width-1-3 padding">
          <button class="button float-middle" @click="getNewColor()">{{ ganaIn ? 'Play again!' : 'New Colors!' }}</button>
        </div>
        <div class="flex width-1-3  padding">
          <h6 class="margin-auto color-red">{{ ganaIn ? 'You picked right!' : '' }}</h6>
        </div>
        <div class="flex width-1-3 text-align-center padding">

          <div class="margin-auto ">
            <button type="button" 
              @click="setDifficulty('E')" 
              class="button difficulty === 'E' ? selected : '' ">
              EASY
            </button>
            <button type="button" 
              @click="setDifficulty('H')" 
              class="button difficulty === 'H' ? selected : '' ">
              HARD
            </button>
          </div>
          
        </div>

      </div>
      
    </div>

  </section>

</template>

<script >

  export default  {
    name: 'src-components-options',
    props: ['ganaIn'],
    mounted () {
      this.getNewColor();
    },
    data () {
      return {
        r: null,
        g: null,
        b: null,
        difficulty: 'H',
        EASY: 3,
        HARD: 6,
        cont: 0,
      }
    },
    methods: {
      setDifficulty(opt){
        this.difficulty = opt;
        this.$emit('difficulty-out', this.difficulty);
      },
      getNewColor() {

        var r = this.randomInt();
        var g = this.randomInt();
        var b = this.randomInt();
        //console.log(this.r, this.g, this.b);
        this.$emit('get-new-color-out', { r:r, g:g, b:b } );
      },
      randomInt(){
        return Math.floor(Math.random() * 256);
      }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .selected{

  }
  .padding{
    padding: 10px;
  }
  .margin-auto{
    margin: 0 auto;
  }
  .float-middle{
    float: middle;
  }
  .float-right{
    float: right;
  }
  .text-align-center{
    
  }
  .width-1-3{
    width: 33.33%;
  }
  .flex{
    display: flex;
  }
  .background{
    background: white;
  }
  .src-components-options {

  }
  .color-red{
    color:red;
  }
  .button{
    border:none;
    border: none;
    height: 40px;
    padding: 10px;

  }
</style>
