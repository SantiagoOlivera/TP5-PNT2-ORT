<template >

  <section class="src-components-select-color">
   <!--  {{ colorIn }}
    {{ correctOption }} -->
    <div class="background" :colorIn="colorIn">
      
      <div class="container grid">
        <div class="square " 
          v-for="(item,index) in blocks" :key="index"
          :style="{ 
            background: ganaIn ? cssRGBColor  : item.background, 
            visibility: ganaIn ? 'visible'    : item.selected ? 'hidden' : 'visible' 
          }"
          @click="selectColor(item)">
        </div>
      </div>

      

    </div>

  </section>

</template>

<script >

  export default  {
    name: 'src-components-select-color',
    props: ['cantBlocksIn', 'colorIn', 'ganaIn'],
    watch: { 
      colorIn() {
        //this.setGana(false);
        this.setCorrectOption();
        this.setBlocks();
      }
    },
    mounted () {
      
    },
    data () {
      return {
        cssRGBColor: null,
        blocks:[],
        correctOption: null,
      }
    },
    methods: {
      setBlocks(){
        this.blocks = [];
        //:style="{ background: getRandomBackgroundColor(index) }"
        for(var i=0; i<this.cantBlocksIn; i++){
          var key = i+1
          this.blocks.push({opt: key, background: this.getRandomBackgroundColor(key), selected: false });
        }
        //console.log(this.blocks);
      },
      setCorrectOption(){
        var min = 1;
        var max = this.cantBlocksIn;
        this.correctOption = this.randomInt(min, max);
        this.cssRGBColor = `rgb(${this.colorIn.r},${this.colorIn.g},${this.colorIn.b})`;
      },
      getRandomBackgroundColor(key){

        var rgbColor = null;

        if( key === this.correctOption ){
          rgbColor = this.cssRGBColor;
        }else{
          var color = this.randomColor();
          rgbColor = `rgb(${color.r},${color.g},${color.b})`
        }

        return rgbColor;

      },
      randomColor(){
        var r = this.randomInt();
        var g = this.randomInt();
        var b = this.randomInt();

        // si sale un color igual al color seleccionado tiramos de nuevo
        while(r === this.colorIn.r && g === this.colorIn.g && b === this.colorIn.b){
          r = this.randomInt();
          g = this.randomInt();
          b = this.randomInt();
        }

        return {r:r, g:g, b:b};
      },
      randomInt(min, max){
        
        var random = null;
        
        if(!min && !max){
          random = Math.floor(Math.random() * 256);
        }else{
          random = min + ( Math.floor(Math.random() * (max - min + 1)) );
        }

        return random;

      },
      selectColor(item){
        if(this.isCorrect(item.opt)){
          console.log("CORRECTO");
          this.win();
        }else{
          item.selected = true;
        }
      },
      isCorrect(opt){
        return opt === this.correctOption;
      },
      win(){
        this.setGana(true);
      },
      setGana(estado){
        this.$emit('gana-out', estado);
      }
    },
    computed: {
    }
}


</script>

<style scoped >

  .invisible{
    visibility:hidden;
  }

  .square {
    visibility:block;
    width: 30%;
    background: blue;
    padding-bottom: 30%;
    float: left;
    margin: 1.66%;
    border-radius: 10%;
    transition: background 0.8s;
    -webkit-transition: background 0.8s;
    -moz-transition: background 0.8s;
  }

  .container {
    margin: 20px auto;
    max-width: 600px;
  }
  .src-components-select-color {
    
  }
</style>
