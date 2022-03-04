<template>
<div class="main">
    <div class="home" :style="currentImage"></div>

    <div id="intro">
        <h1> IK<span>BO</span></h1>
        <p> <span>COVERAGE &</span> PHOTOGRAPHY</p>
    </div>
    <transition name="list" appear >
      <div id="floatBtn" >
        <v-btn color="green" fab large dark @click="whatsappFunction">
            <v-icon x-large>mdi-whatsapp</v-icon>
        </v-btn>
      </div>
    </transition>
     <a id="whatslink" ref="whatsapp" href="https://api.whatsapp.com/send?phone=+2347031228335">Click to connect +506 0000 0000</a>
      
</div>
      
      
</template>

<script>
// import Nav from '../components/Nav.vue'

export default {
 components: {  },
  data() {
    return{
      currentSlide: 0,
      num: ['one', 'four', 'eight', 'eighteen', 'fifteen', 'fourteen', 'nine', 
      'nineteen', 'thirty', 'thirtyone', 'thirtytwo', 'twentyseven','twentythree', 'two']
    }
  },
  methods: {
    sliding() {
        setInterval(() => {
          this.next()
        }, 4000)
      },
    
    next() {
      if (this.currentSlide >= this.num.length-1) {
        this.currentSlide = 0
      } else{
        this.currentSlide++
      }
      
    },
    whatsappFunction() {
      this.$refs.whatsapp.click();
    }
  },
  mounted() {
    this.sliding()
  },
  computed: {
    currentImage() {
      return {'background-image': 'url(' + require('../assets/slides/' + this.num[this.currentSlide] + '.jpg') + ')'}
    }
  }
  
}
</script>

<style>
  .main{
    position: relative;
  }
  .home{
    background-color: white;
    background-size: cover;
    background-position: center;
    height: 100vh;
    width: 100vw;
    border: 2px solid black;
    position: relative;
    animation: zoom 4s linear infinite; 
  }

  @keyframes zoom{
    0% { opacity: 0}
    15% { opacity: 0.5 }
    50% { opacity: 1 }
    85% { opacity: 0.5 }
    100% { opacity: 0}
  }

  #intro{
    position: absolute;
    top: 50%;
    right: 10px;
    transform: translateY(-50%);
    background: rgba(0, 0, 0, 0.050); 
    color: white;
    text-align: right;
  }

  #intro h1{
    font-size: 60px; 
    margin: 0;
  }

  #intro h1 span{
    color: orangered;
  }

  #intro p{
    font-weight: 700;
  }
  #intro p span{
    color: orangered;
  }

  
</style>

/* 
@keyframes zoom{
    0% { transform: scale(1.5); opacity: 0}
    15% { transform: scale(1.2); opacity: 0.5 }
    50% { transform: scale(1); opacity: 1 }
    85% { transform: scale(1.2); opacity: 0.5 }
    100% { transform: scale(1.5); opacity: 0}
  }

  <v-btn 
                color="green"
                fab fixed
                large
                dark
                bottom
                right
                class="v-btn--example">
                <v-icon x-large>mdi-whatsapp</v-icon>
              </v-btn>

*/