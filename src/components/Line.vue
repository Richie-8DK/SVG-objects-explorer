<template>
  <div>
    <svg id="svg" width="300" height="300">
      <line
      :stroke="stroke"
      :stroke-width="stroke_width"
      :x1="x1"
      :y1="y1"
      :x2="x2"
      :y2="y2" />

      <dragger
      :x.sync="x1"
      :y.sync="y1"/>
      <dragger
      :x.sync="x2"
      :y.sync="y2"/>
    </svg><br/>

    <div class="form">
      x1: <input v-model="x1" type="range" max="300"><br/>
      y1: <input v-model="y1" type="range" max="300"><br/>
      x2: <input v-model="x2" type="range" max="300"><br/>
      y2: <input v-model="y2" type="range" max="300"><br/>
      stroke-width: <input v-model="stroke_width" type="range" max="100"><br/>
      stroke: <input v-model="stroke" type="color">

      <p>&lt;line x1="{{x1}}" y1="{{y1}}" x2="{{x2}}" y2="{{y2}}" stroke="{{stroke}}" stroke-width:"{{stroke_width}}" /&gt;</p>
    </div>
  </div>
</template>

<script>
  import dragger from './Dragger.vue'

  export default({
    name: 'myline',
    data () {
      return {
        width: 200,
        height: 100,
        x1: 0,
        y1: 20,
        x2: 100,
        y2: 130,
        stroke: '#BBC42A',
        stroke_width: 8
      }
    },
    components: {
      dragger
    }
  })
</script>
