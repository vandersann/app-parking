<template>
  <Navebar :logo="logo_src" :alt="app_name" />
  <router-view/>
  <Footer />

</template>

<script>
import Navebar from './components/Navebar.vue';
import Footer from './components/Footer.vue';

export default {
  components: {
    Navebar,
    Footer,
  },
  data() {
    return{
      logo_src: "/img/icon.png",
      app_name: "Cadastre o Veículo"
    }
  }
}
</script>

<style>
  * {
    font-family: Arial, Helvetica, sans-serif;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  main {
    margin-top: 20px;
    min-height: 100%;
    display: block;
    min-height: 100vh;
    min-height: -webkit-calc(100vh - 100px);
    min-height: -moz-calc(100vh - 100px);
    min-height: calc(100vh - 100px);
    position: relative;
    width: 100%;
  }

  main .bg {
    position: absolute;
    z-index: -1;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background: url('/public/img/background.jpg') top right, center no-repeat fixed ;
    background-size: cover;
    opacity: .3;
      width: 100%;
      height: 100%;
  }


  h1 {
    text-align: center;
    font-size: 42px;
    margin-bottom: 30px;
    color: #222;
  }
</style>
