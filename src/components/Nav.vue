<template>
    <nav>
        <v-app-bar absolute clipped-left flat dense id="navbar" color="rgba(0,0,0,0.050)" class="align-center">
            <router-link to="/"><img src="../assets/logo.jpg" class="mainLogo" alt=""></router-link>
            <v-spacer></v-spacer>
            <v-app-bar-nav-icon class="d-md-none white--text" @click="navdrawer = !navdrawer"></v-app-bar-nav-icon> 
        </v-app-bar>

        <v-navigation-drawer absolute clipped class="white--text" color="info" v-model="navdrawer">
            <v-list dense shaped>
              <v-list-item-group  color="primary">
                <v-list-item v-for="(link) in links" :key="link.text" :to="link.route" class="my-3 white--text">
                  <v-list-item-icon>
                    <v-icon class="white--text" v-text="link.icon"></v-icon>
                  </v-list-item-icon>
                  <v-list-item-content>
                    <v-list-item-title v-text="link.text"></v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list-item-group>
            </v-list>
        </v-navigation-drawer>

      </nav>  
    
</template>
-
<script>
export default {
    data() {
    return{
      navdrawer: false,
      links: [
        {icon: 'mdi-home', text: 'Home', route: '/'},
        {icon: 'mdi-folder-multiple-image', text: 'Gallery', route: '/gallery'},
        {icon: 'mdi-tools', text: 'Our Services', route: '/services'},
        {icon: 'mdi-phone', text: 'Contact', route: '/contact'},
      ]
    }
  }
}
</script>

<style>
   #navbar{
       color: white;
   }
   .mainLogo{
     width: 60px;
   }
   a.router-link-active{
     display: flex;
     align-items: center;
   }
</style>