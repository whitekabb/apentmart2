<template>
  <div id="app" class="body main">
    <Navbar/>
    <!-- <div class="container"> -->
      <div class="test-min-height">
      <router-view/>
      </div>
    <!-- </div> -->
    <Footer/>
  </div>
</template>

<script>
import Navbar from './components/Navbar'
import Footer from './components/Footer'
export default {
  name: 'App',
  components: {
    Navbar,
    Footer
  }
}
</script>

<style>
.test-min-height{
 min-height: 459px;
}
</style>
