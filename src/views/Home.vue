<template>
<div class="main">
    <div class="slider" ref="slidecon">
      <transition-group :name=name mode="out-in">
        <div v-show="index == currentIndex" 
            v-for="(slide, index) in slides" 
            :key="slide.src" >
            <img :src="slide.src" alt="">
        </div>
      </transition-group>
    </div>
    <div id="slideBtn">
        <v-btn fab small class="white black--text" @click="prev">
            <v-icon>mdi-arrow-left-bold</v-icon>
        </v-btn>
        <div class="slideindicator">
          <span v-for="(slide, index) in slides" :key="slide.src" :class="{active: index == currentIndex}"></span>
        </div>
        <v-btn fab small class="white black--text" @click="next">
            <v-icon>mdi-arrow-right-bold</v-icon>
        </v-btn>
    </div>

    <div id="intro">
        <h1> IK<span>BO</span></h1>
        <p> <span>COVERAGE &</span> PHOTOGRAPHY</p>
    </div>
    
    
    
    <transition name="list" appear="">
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

export default {
 components: {  },
  data() {
    return{
      currentIndex: Math.floor(Math.random() *10),
      slideTimer: '',
      name: 'left',
      touch: {
        startX: 0,
        endX: 0
      },
      slides: [
        {src: require('../assets/slides/eight.jpg')},
        {src: require('../assets/slides/eighteen.jpg')},
        {src: require('../assets/slides/fourteen.jpg')},
        {src: require('../assets/slides/one.jpg')},
        {src: require('../assets/slides/thirtyone.jpg')},
        {src: require('../assets/slides/thirtytwo.jpg')},
        {src: require('../assets/slides/nineteen.jpg')},
        {src: require('../assets/slides/twentyseven.jpg')},
        {src: require('../assets/slides/twentythree.jpg')},
        {src: require('../assets/slides/twentytwo.jpg')},
        {src: require('../assets/slides/two.jpg')}
      ]
    }
  },
  methods: {
    whatsappFunction() {
      this.$refs.whatsapp.click();
    },
    next() {
      if( this.currentIndex >= this.slides.length-1) {
        this.currentIndex = 0
      } else {
        this.currentIndex++
      }
      this.name = 'left'
      this.resetInterval()
    },
    prev() {
      if( this.currentIndex <= 0) {
        this.currentIndex = this.slides.length-1
      } else {
        this.currentIndex--
      }
      this.name = 'right'
      this.resetInterval()
    },
    resetInterval() {
      clearInterval(this.slideTimer)
      this.sliding()
    },
    sliding() {
      this.slideTimer = setInterval(() => {
        this.next()
      }, 7000)
    },
    touchstart(event) {
      this.touch.startX = event.touches[0].clientX;
      this.touch.endX = 0;
    },
    touchmove(event) {
      this.touch.endX = event.touches[0].clientX;
    },
    touchend() {
      if(this.touch.endX > this.touch.startX) {
        this.prev()
        this.resetInterval()
      } else{
        this.next() 
        this.resetInterval()
      }
    }
  },
  mounted() {
    this.sliding() 
    let slider = this.$refs.slidecon;
    slider.addEventListener('touchstart', (event) => {this.touchstart(event)})
    slider.addEventListener('touchmove', (event) => {this.touchmove(event)})
    slider.addEventListener('touchend', () => {this.touchend()})
  },
  computed: {
    
  }
  
}
</script>

<style>
  .main{
    position: relative;
    border: 1px solid red;
    height: 100vh;
    overflow: hidden;
  }

  .slider{
    height: 100%;
    display: flex;
    position: relative;
  }

  .slider div{
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
  }

  .slider div img{
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
  }

  
  .left-leave{
    transform: translateX(0%);
  }
  .left-leave-to{
    transform: translateX(-100%);
  }
  .left-leave-active{
    transition: all .5s ease;
  }
  .left-enter-active{
    animation: slideinleft .5s ease;
  }

  @keyframes slideinleft{
      0%  { transform: translateX(100%);}
      100% { transform: translateX(0%);}
  }

  .right-leave{
    transform: translateX(0%);
  }
  .right-leave-to{
    transform: translateX(100%);
  }
  .right-leave-active{
    transition: all .5s ease;
  }
  .right-enter-active{
    animation: slideinright .5s ease;
  }

  @keyframes slideinright{
    0%  { transform: translateX(-100%);}
    100% { transform: translateX(0%);}
  }


  
  #slideBtn{
    width: 80%;
    max-width: 400px;
    position: absolute;
    bottom: 150px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    justify-content: space-between;
  }

  .slideindicator{
    width: 60%;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .slideindicator span{
    width: 10px;
    height: 10px;
    border-radius: 10px;
    background:rgba(0, 0, 0, 0.450);
    transition: all .5s ease;
  }

  .slideindicator span.active{
    width: 20px;
    height: 20px;
    border-radius: 20px;
    background:crimson;
  }

  #intro{
    position: absolute;
    top: 50%;
    right: 10px;
    transform: translateY(-50%);
    background: rgba(0, 0, 0, 0.400); 
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

<div class="home" :style="currentImage"></div>
animation: zoom 4s linear infinite;










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



*/