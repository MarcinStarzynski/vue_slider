<template>
  <div>
    <HelloWorld msg="Simple slider component"/>
  </div>
</template>

<script>
import HelloWorld from './components/Homepage.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
  }
}
</script>

<style lang='scss'>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 12px;
  }
  body {
      &::before {
      content: '';
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(#fff 15%, #000);
      clip-path: polygon(81% 0, 0 35%, 0 0);
      }
      &::after {
      content: '';
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: -1;
      background: linear-gradient(#000 5% ,#fff);
      clip-path: polygon(100% 65%, 19% 100%, 100% 100%);
      }
    background-image: linear-gradient(#fff 5%, #000);
    display: flex;
    justify-content: center;
    background-repeat: no-repeat;
    background-position: right top;
    background-attachment: fixed;
    align-items: center;
  }
</style>
