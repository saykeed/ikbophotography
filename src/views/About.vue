<template>
  <div class="about">
      <div class="aboutHead">
            <h1>About <br> Us</h1>
      </div>
      <div class="aboutbody">
            <h1>About <br> Us</h1>
      </div>
      <transition name="list" appear >
        <div id="floatBtn">
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
      methods: {
        whatsappFunction() {
          this.$refs.whatsapp.click();
        }
      }
    }
</script>

<style>
.about{
    width: 100%;
  }
  .aboutHead{
    background: url(../assets/img/nineteen.jpg);
    background-size: cover;
    background-position: center;
    height: 400px;
    width: 100%;
    color: white;
    padding: 10px;
    position: relative;
  }

  .aboutHead h1{
    position: absolute;
    bottom: 30px;
  }
</style>