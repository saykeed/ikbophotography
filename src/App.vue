<template>
  <v-app>
    <Nav v-if="$route.name == 'Home'" />
    <FixedNav v-if="$route.name !== 'Home'"/>
    
    <v-main id="pagebox">
     
      <router-view/>
        
    </v-main>
  </v-app>
</template>

<script>
import Nav from './components/Nav.vue'
import FixedNav from './components/FixedNav.vue'
export default {
  name: 'App',
  components: { Nav, FixedNav}
};
</script>
<style>
  
</style>