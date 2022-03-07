<template>
  <div class="gallery">
    <Modal v-if="dialog" :selected="selected" @onclose="showModal"/>
      <v-container class="align-center" >
          <div id="test">
              <img src="../assets/img/one.jpg" @click="showModal('one')" alt="">
              <img data-aos="fade-left" src="../assets/img/two.jpg" @click="showModal('two')" alt="">
              <img data-aos="fade-right" src="../assets/img/three.jpg" @click="showModal('three')"  alt="">
              <img data-aos="zoom-in" src="../assets/img/four.jpg" @click="showModal('four')" alt="">
              <img data-aos="slide-up" src="../assets/img/five.jpg" @click="showModal('five')" alt="">
              <img data-aos="zoom-out-right" src="../assets/img/six.jpg" @click="showModal('six')" alt="">
              <img data-aos="flip-up" src="../assets/img/seven.jpg" @click="showModal('seven')" alt="">
              <img data-aos="fade-left" src="../assets/img/eight.jpg" @click="showModal('eight')" alt="">
              <img data-aos="fade-right" src="../assets/img/nine.jpg" @click="showModal('nine')" alt="">
              <img data-aos="zoom-in" src="../assets/img/ten.jpg" @click="showModal('ten')" alt="">
              <img data-aos="slide-up" src="../assets/img/eleven.jpg" @click="showModal('eleven')" alt="">
              <img data-aos="zoom-out-right" src="../assets/img/twelve.jpg" @click="showModal('twelve')" alt="">
              <img data-aos="flip-up" src="../assets/img/thirteen.jpg" @click="showModal('thirteen')" alt="">
              <img data-aos="fade-left" src="../assets/img/fourteen.jpg" @click="showModal('fourteen')" alt="">
              <img data-aos="fade-right" src="../assets/img/fifteen.jpg" @click="showModal('fifteen')" alt="">
              <img data-aos="zoom-in" src="../assets/img/sixteen.jpg" @click="showModal('sixteen')" alt="">
              <img data-aos="slide-up" src="../assets/img/seventeen.jpg" @click="showModal('seventeen')" alt="">
              <img data-aos="zoom-out-right" src="../assets/img/eighteen.jpg" @click="showModal('eighteen')" alt="">
              <img data-aos="flip-up" src="../assets/img/nineteen.jpg" @click="showModal('nineteen')" alt="">
              <img data-aos="fade-left" src="../assets/img/twenty.jpg" @click="showModal('twenty')" alt="">
              <img data-aos="fade-right" src="../assets/img/twentyone.jpg" @click="showModal('twentyone')" alt="">
              <img data-aos="zoom-in" src="../assets/img/twentytwo.jpg" @click="showModal('twentytwo')" alt="">
              <img data-aos="slide-up" src="../assets/img/twentythree.jpg" @click="showModal('twentythree')" alt="">
              <img data-aos="zoom-out-right" src="../assets/img/twentyfour.jpg" @click="showModal('twentyfour')" alt="">
              <img data-aos="flip-up" src="../assets/img/twentyfive.jpg" @click="showModal('twentyfive')" alt="">
              <img data-aos="fade-left" src="../assets/img/twentysix.jpg" @click="showModal('twentysix')" alt="">
              <img data-aos="fade-right" src="../assets/img/twentyseven.jpg" @click="showModal('twentyseven')" alt="">
              <img data-aos="zoom-in" src="../assets/img/twentyeight.jpg" @click="showModal('twentyeight')" alt="">
              <img data-aos="slide-up" src="../assets/img/twentynine.jpg" @click="showModal('twentynine')" alt="">
              <img data-aos="zoom-out-right" src="../assets/img/thirty.jpg" @click="showModal('thirty')" alt="">
              <img data-aos="flip-up" src="../assets/img/thirtyone.jpg" @click="showModal('thirtyone')" alt="">
              <img data-aos="fade-left" src="../assets/img/thirtytwo.jpg" @click="showModal('thirtytwo')" alt="">
              <img data-aos="fade-right" src="../assets/img/thirtythree.jpg" @click="showModal('thirtythree')" alt="">
          </div>
          <transition name="list" appear >
            <div id="floatBtn">
              <v-btn color="green" fab large dark @click="whatsappFunction">
                  <v-icon x-large>mdi-whatsapp</v-icon>
              </v-btn>
            </div> 
          </transition>
          <a id="whatslink" ref="whatsapp" href="https://api.whatsapp.com/send?phone=+2347031228335">Click to connect +506 0000 0000</a>
      </v-container>
  </div>
</template>

<script>
import Modal from '../components/Modal.vue'
export default {
  components: { Modal },
  data () {
    return{
      dialog: false,
      selected: null
    }
  },
  methods: {
    showModal(index ) {
      this.dialog = !this.dialog
      this.selected = index
    },
    whatsappFunction() {
      this.$refs.whatsapp.click();
    }
  }
  
}
</script>

<style>
  .gallery{
    width: 100%;
  }

  #test{
    width: fit-content;
    max-width: 500px;
    height: auto;
    margin: 0 auto;
    overflow: hidden;
  }

  .gallery img{
    width: 100%;
    max-width: 500px;
    height: 100%;
    object-fit: cover;
    object-position: center;
    margin: 20px auto;
  }
</style>

/*


*/