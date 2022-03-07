<template>
  <div class="contact">
      <a ref="phone" href="tel:07031228335">Call us at 866-556-2570</a>
      <a ref="whatsapp" href="https://api.whatsapp.com/send?phone=+2347031228335">Click to connect +506 0000 0000</a>
      <a ref="email" href="mailto:Ikbo@gmail.com">Send email</a>

      <AddressModal  v-if="address" :address="address" @closeModal="contactIkbo('Address')"/>
      <p>Tel: 07031228335</p>
      <p>Whatsapp: 07031228335</p>
      <p>Email: Ikbo@gmail.com</p>


      <transition-group tag="div" class="optionBox"
      appear
      @before-enter="beforeEnter"
      @enter="enter"
      >
        <div class="contactoptions" v-for="(option, index ) in options" :key="option.text" @click="contactIkbo(option.text)" :data-index="index">
          <v-icon >{{ option.icon }}</v-icon>
          <h3>{{ option.text }}</h3>
        </div>
      </transition-group>

  </div>
</template>

<script>
import gsap from 'gsap'
import AddressModal from '../components/AddressModal.vue'

export default {
  components: { AddressModal },
  data() {
    return{
      address: false,
      options: [
        {text: 'Phone', icon: 'mdi-phone' },
        {text: 'Whatsapp', icon: 'mdi-whatsapp'},
        {text: 'Email', icon: 'mdi-email'},
        {text: 'Address', icon: 'mdi-map-marker'}
      ]
    }
  },
  methods: {
    contactIkbo(x) {
      if(x === 'Phone') {
        this.$refs.phone.click()
      } else if(x === 'Whatsapp') {
        this.$refs.whatsapp.click()
      } else if(x === 'Email') {
        this.$refs.email.click()
      } else if(x === 'Address') {
        this.address = !this.address
      }
    },
    beforeEnter(el) {
      el.style.opacity = 0
      el.style.transform = 'translateY(70px)'
    },

    enter(el, done) {
      gsap.to(el, {
        duration: 1.2,
        y: 0,
        opacity: 1,
        onComplete: done,
        delay: 0.5 * el.dataset.index
      })
    }
  }
}
</script>

<style>
  .contact{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    width: 100vw;
  }
 .contact a{
   display: none;
 }

 .contact p{
   margin: 0px auto;
 }

  .optionBox{
    width: 100%;
    max-width: 500px;
    padding: 10px;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-between;
  }
  .contactoptions{
    text-align: center;
    width: 44%;
    height: 140px;
    margin: 3%;
    box-shadow: 2px 2px 3px rgba(0,0,0,0.200), -2px -2px 3px rgba(0,0,0,0.100);
    border-radius: 20px;
    cursor: pointer;
  }
  .contactoptions .v-icon{
    color: orangered;
    font-size: 60px;
    margin: 10px auto;
  }

  .contactoptions:active{
    background: black;
    color: white;
  }

  .contactoptions:active .v-icon{
    color: white;
  }

  /*for the responsieve screen of md*/
    @media screen and (min-width:960px){
        .contactoptions:hover{
          background: black;
          color: white;
        }

        .contactoptions:hover .v-icon{
          color: white;
        }
    }

  
</style>

/*
  <a href="tel:8665562570">Call us at 866-556-2570</a>
*/