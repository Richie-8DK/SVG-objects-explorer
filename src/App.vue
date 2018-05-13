<template>
  <div id="app">
    <myrect class="explorer"/>
    <mycircle class="explorer"/>
    <myellipse class="explorer"/>
    <myline class="explorer"/>
    <mypolyline class="explorer"/>
    <mypolygon class="explorer"/>
  </div>
</template>

<script>
import myrect from './components/Rect.vue'
import mycircle from './components/Circle.vue'
import myellipse from './components/Ellipse.vue'
import myline from './components/Line.vue'
import mypolyline from './components/Polyline.vue'
import mypolygon from './components/Polygon.vue'

export default {
  name: 'app',
  components: {
    myrect,
    mycircle,
    myellipse,
    myline,
    mypolyline,
    mypolygon
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}


  svg {
    width: 300px;
    height: 300px;
    float: left;
  }
  .form {
    margin-left: 15%;
    min-height: 300px;
  }
</style>
