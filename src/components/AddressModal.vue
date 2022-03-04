<template>
    <div class="addressmodal">
        
        <v-dialog v-model="address"  max-width="500" overlay-color="black"          overlay-opacity="0.8" close-delay="500" persistent>
                
            <div id="addressInfo"> 
                <v-btn fab x-small  class="my-3" @click="closeAddressModal">
                    <v-icon>mdi-close</v-icon>
                </v-btn>
                <h3><span>Ikbo Photography</span> is located at 20, Owoseni Street, Temidire, Sango, Ogun State, Nigeria </h3>
            </div>
        </v-dialog>
    </div>
</template>

<script>
export default {
    props: [ 'address' ],
    methods: {
        closeAddressModal() {
            this.$emit('closeModal')
        
        }
    }
}
</script>

<style>
    #addressInfo{
        background: white;
        color: black;
        padding: 20px;
        text-align: center;
    }
    #addressInfo h3 span{
        color: red;
    }
</style>