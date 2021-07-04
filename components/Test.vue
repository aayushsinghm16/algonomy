<!-- Please remove this file from your project -->
<template>
  <section class="">
    <p class="heading">Shuffle and Sort</p>
    <!-- <img src="~/assets/images/vueJsAssignment.png" alt=""> -->
    <div class="main-container">
      <div class="buttons-container">
        <button @click.stop="shuffleArray()">Shuffle</button>
        <button @click.stop="numbers.sort()">Sort</button>
      </div>
      <div class="cards-container" id="cards-container">
        <div class="cards" v-for="item in numbers" :key="item">
          {{item}}
        </div>
      </div>
    </div>
  </section>
</template>
<script>
export default {
  data() {
    return {
      numbers:[1,2,3,4,5,6,7,8,9]
    }
  },
  methods: {
    shuffleArray() {

      for (var i = this.numbers.length - 1; i > 0; i--) {
        var j = Math.floor(Math.random() * (i + 1));
        var temp = this.numbers[i];
        this.$set(this.numbers, i ,this.numbers[j]);
        this.$set(this.numbers, j ,temp);
      }   
    },
  },
}
</script>
<style lang="scss" scoped>
section{
  .heading{
    text-align: center;
    font-size: 1rem;
    background: #323232;
    color: white;
    margin: 0px;
    padding: 0.625rem 0px;
    @media (min-width: 960px)  {
      background: white;
      color: black;
    }
  }
  .main-container{
    padding-top:10px ;
    background: none;
    .buttons-container{
      text-align: center;
      button{
        background: #72c3dc;
        border: none;
        // padding: 0.5rem;
        border-radius: 4px;
        box-shadow: 0px 4px 0px 0px #45a0bc;
        color: white;
        width: 3.75rem;
        height: 1.875rem;

      }
    }
    .cards-container{
      padding: 1rem;
      .cards{
        background: #eeeeee;
        margin-bottom: 0.5rem;
        text-align: center;
        padding: 0.5rem;
        border-left: 5px solid;
      }
      $colors: #6f98a8,#2c8ead, #2f454e ,#bfbfbf;

      @for $i from 1 through length($colors) {
        .cards:nth-child(#{length($colors)}n+#{$i}) {
          border-color: nth($colors, $i);
          @media (min-width: 960px){
            border: none;
            background: nth($colors, $i);
          }
        }
      }
      
    }
    @media (min-width: 960px)  {
      background: #efefef;
      display: grid;
      grid-template-columns: 75% 25%;
      padding-top: 0px;
      .buttons-container{
        grid-column: 2/3;
        grid-row: 1/2;
        padding: 1rem;
        button{
          display: block;
          width: 100%;
          margin-bottom: 1rem;
        }
      }
      .cards-container{
        display: grid;
        grid-column: 1/2;
        grid-row: 1/2;
        grid-template-columns: repeat(3, 1fr);
        padding: 0px;
        margin: 0px;
        .cards{
          padding: 0px;
          margin: 0px;
          font-size: calc((100vh/3) - 50px);
          color: white;
        }
      }
    }
  }
 
  @media (min-width: 960px)  {
    height: 100vh;
    width: 100vw;
    display: grid;
    grid-template-rows: max-content 1fr;
  }
}

</style>
