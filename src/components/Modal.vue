<template>
    <v-dialog v-model="dialog"  max-width="500" overlay-color="black" overlay-opacity="0.8" close-delay="500">
        <div id="modal">  
            <div id="modalHeader">
                <v-btn fab x-small class="white black--text mx-1" @click="play">
                    <v-icon>{{ playStatus }}</v-icon>
                </v-btn>
                <v-btn fab x-small class="white black--text mx-1" @click="closeModal">
                    <v-icon>mdi-close</v-icon>
                </v-btn>
            </div>
            <div v-if="playSlideshow" id="lower"><div id="upper"></div></div>
           
              <div id="imgbox">
                <img id="imgModal" ref="imgbox" :src="currentImg" alt="">
              </div>
            
            <div id="modalBtn">
                <v-btn fab small class="white black--text" @click="prev">
                    <v-icon>mdi-arrow-left-bold</v-icon>
                </v-btn>
                <v-spacer></v-spacer>
                <v-btn fab small class="white black--text" @click="next">
                    <v-icon>mdi-arrow-right-bold</v-icon>
                </v-btn>
            </div> 
        </div>
    </v-dialog>
</template>

<script>

export default {
    props: [ 'selected' ],
    data() {
        return{
            dialog: true,
            playSlideshow: false,
            currentSlide: 0,
            timer: null,
            images: ['one', 'two', 'three', 'four', 'five', 'six', 'seven',
                    'eight', 'nine', 'ten', 'eleven', 'twelve', 'thirteen', 'fourteen',
                    'fifteen', 'sixteen', 'seventeen', 'eighteen', 'nineteen', 'twenty', 'twentyone',
                    'twentytwo', 'twentythree', 'twentyfour', 'twentyfive', 'twentysix', 'twentyseven',
                    'twentyeight', 'twentynine', 'thirty', 'thirtyone', 'thirtytwo', 'thirtythree']
        }
    },
    methods: {
        
        closeModal() {
            this.$emit('onclose')
        },
        next() {
            let imgbox = this.$refs.imgbox
            imgbox.style.animation = 'slideoutleft .3s ease'
            setTimeout(() => {
                if (this.currentSlide >= this.images.length-1) {
                        this.currentSlide = 0
                } else {
                    this.currentSlide++
                }  
                
            }, 100)
            setTimeout(() => {
                imgbox.style.animation = 'slideinleft .3s ease'
            }, 100)

            if (this.playSlideshow == true) {
                this.clear()
            }
            
        },
        prev() {
            let imgbox = this.$refs.imgbox
            imgbox.style.animation = 'slideoutright .3s ease'
            setTimeout(() => {
                if (this.currentSlide <= 0) {
                    this.currentSlide = this.images.length-1
                } else{
                    this.currentSlide--
                } 
                
            }, 100)
            setTimeout(() => {
                imgbox.style.animation = 'slideinright .3s ease'
            }, 100)
            
            if (this.playSlideshow == true) {
                this.clear()
            }
        },
        play() {
            if (this.playSlideshow == false) {
                 this.timer =  setInterval(() => {
                    let imgbox = this.$refs.imgbox
                    imgbox.style.animation = 'slideoutleft .3s ease'
                    setTimeout(() => {
                        if (this.currentSlide >= this.images.length-1) {
                                this.currentSlide = 0
                        } else {
                            this.currentSlide++
                        }  
                        
                    }, 100)
                    setTimeout(() => {
                        imgbox.style.animation = 'slideinleft .3s ease'
                    }, 100)
                }, 3000)
                this.playSlideshow = !this.playSlideshow
            } else {
                this.clear()
            }

          
        },
        clear() {
            clearInterval(this.timer)
            this.playSlideshow = !this.playSlideshow
        }
        
    },
    mounted() {
        this.currentSlide = this.images.indexOf(this.selected)
       
    },
    computed: {
        currentImg() {
            return require('../assets/img/' + this.images[this.currentSlide] + '.jpg')
        },
        playStatus() {
            if(this.playSlideshow == false) {
                return 'mdi-play'
            } else {
                return 'mdi-pause'
            }
        }
    }

}
</script>

<style>

    #modal{
        padding: 10px 20px;
        text-align: center;
        background: black;
        overflow: hidden;
    }
    #modalHeader{
        margin: 10px auto 20px;
        text-align: right;
    }

    #lower{
        width: 100%;
        height: 5px;
        border-radius: 5px;
        background: rgba(255, 255, 255, 0.213);
        overflow: hidden;
    }
    
    #upper{
        height: 100%;
        background: rgb(90, 162, 172);
        animation: loading 3s linear infinite;
    }

    @keyframes loading{
        0% { width: 0}
        100% { width: 100%}
    }

    #imgbox{
        height: 400px;
        display: flex;
        align-items: center; 
    }
    #imgModal{
        width: 80%;
        height: auto;
        max-height: 80%; 
        object-fit: cover;
        object-position: center;
        margin: 0 auto;
    }
    @keyframes slideoutleft{
        0% { transform: translateX(0px); opacity: 1;}
        100% { transform: translateX(-300px); opacity: 0;}
    }

    @keyframes slideinleft{
        0% { transform: translateX(400px);}
        100% { transform: translateX(0px);}
    }

    @keyframes slideoutright{
        0% { transform: translateX(0px); opacity: 1;}
        100% { transform: translateX(300px); opacity: 0;}
    }
    
    @keyframes slideinright{
        0% { transform: translateX(-400px);}
        100% { transform: translateX(0px);}
    }
    #modalBtn{
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin: 10px auto;
    }
    
</style>