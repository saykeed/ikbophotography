<template>
  <div class="services">
        <div class="serviceHead">
            <h1>Our <br> Services</h1>
        </div>
        <div class="servicebody">
            <div class="serviceintro">
                <p>We offer the full spectrum of Media services. From creating standard Wedding photography experience to Fashion and Potrait Photography to Video Production.</p>
            </div>
            <div id="hypedivs">
                <div id="hype" data-aos="slide-up">
                    <div id="hypeicon">
                        <v-icon size="60">mdi-account-multiple</v-icon>
                    </div>
                    <h2>Wedding Photography</h2>
                    <p>The people who hire me as a wedding photographer hire me not just because of my photographic style, they hire me because of the style of my personality. My style and personality match, so they know they're getting a genuine style.</p>
                </div>
                <div id="hype" data-aos="slide-up">
                    <div id="hypeicon">
                        <v-icon size="60">mdi-account-circle</v-icon>
                    </div>
                    <h2>Potrait Photography</h2>
                    <p>At Ikbo photography and coverage, you are our super star and all activities at the studio is geared towards making you comfortable.</p>
                </div>
                <div id="hype" data-aos="slide-up">
                    <div id="hypeicon">
                        <v-icon size="60">mdi-video-vintage</v-icon>
                    </div>
                    <h2>Video Production</h2>
                    <p>Cinematography and movie production is one area we specialize in. With Ikbo's state of the art video studio your production is ready to roll. </p>
                </div>
            </div>
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
    .services{
    width: 100%;
  }
    .serviceHead{
        background: url(../assets/img/eight.jpg);
        background-size: cover;
        background-position: center top;
        height: 500px;
        width: 100%;
        color: white;
        padding: 10px
    }
    .serviceHead h1{
        line-height: 40px;
    }
    .servicebody{
        background: black;
        padding: 10px;
        text-align: center;
        color: white;
    }
    .servicebody p{
        font-size: 15px;
    }
    .serviceintro {
        max-width: 400px;
        margin: 40px auto;
    }
    #hype{
        margin: 50px auto;
        max-width: 400px;
    }
    #hype h2{
        margin: 15px auto;
    }
    #hypeicon{
        width: 100px;
        height: 100px;
        border-radius: 30px;
        margin: 20px auto;
        display: flex;
        align-items: center;
        justify-content: center;
        transition: all .3s linear;
    }
    #hypeicon .v-icon{
        color: white;
        transition: all .5s linear;
    }
    #hype:hover #hypeicon{
        background: white;
    }
    #hype:hover #hypeicon .v-icon{
        color: black;
    }

    /*for the responsieve screen of md*/
    @media screen and (min-width:960px){
        #hypedivs{
            display: flex;
            justify-content: space-between;
        }

        #hype{
            width: 30%;
        }
    }
    
</style>