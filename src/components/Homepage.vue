<template>
  <div class="style">
    <h4>{{ msg }}</h4>
    <Slider />
  </div>
  
</template>

<script>
import Slider from './Slider.vue'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components: {
    Slider,
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='scss'>
  .style {
    h4 {
      margin: 12px auto 24px auto;
    }
    color: rgb(41, 34, 34);
    font-size: 45px;
    font-weight: bold;
    position: relative;
    margin: 0 auto;
    text-align: center;
  }

  @media (min-width: 320px) and (max-width: 720px) {
    h4 {
      font-size: 20px;
    }
  }
</style>
