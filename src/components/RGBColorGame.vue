<template >
  <div>
    <HeaderRGBColor 
      :color-in="{r:r, g:g, b:b}" 
      :gana-in="gana"
    />
    <Options 
      @difficulty-out="setDifficulty($event)" 
      @get-new-color-out="setColor($event)"
      :gana-in="gana"
    />
    <SelectColor 
      :cant-blocks-in="cantBlocks" 
      :color-in="{r:r, g:g, b:b}"
      :gana-in="gana"
      @gana-out="setGana($event)"
    /> 
  </div>
 
</template>

<script>

  import SelectColor from './SelectColor.vue';
  import Options from './Options.vue';
  import HeaderRGBColor from './HeaderRGBColor.vue'; 

  export default  {
    name: 'RGBColorGame',
    components: {
      HeaderRGBColor,
      Options,
      SelectColor,
    },
    props: [],
    mounted () {
      
    },
    data () {
      return {
        r: null,
        g: null,
        b: null,
        cantBlocks: 6,
        difficulty: 0,
        HARD: 6,
        EASY: 3,
        gana: false,  
      }
    },
    methods: {
      setDifficulty(difficulty) {
        if(difficulty === 'E'){
          this.cantBlocks = this.EASY
        }else if(difficulty === 'H'){
          this.cantBlocks = this.HARD
        }
      },
      setColor(color) {
        this.setGana(false);
        this.r = color.r;
        this.g = color.g;
        this.b = color.b;
      },
      setGana(estado){
        //console.log("ESTADO", estado);
        this.gana = estado;
      },
    },
    computed: {

    }
}


</script>

<style>
  
</style>
