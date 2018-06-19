<template>
  <div>
    <svg id="svg" width="300" height="300">
      <rect
      :stroke="stroke_seen ? stroke : ''"
      :stroke-width="stroke_seen ? stroke_width : ''"
      :width="width"
      :height="height"
      :fill="fill"
      :x="x"
      :y="y"
      :rx="rx"
      :ry="ry" />
      <dragger
      :x.sync="x"
      :y="y+height/2"/>
      <dragger
      :x="x+width/2"
      :y.sync="y"/>
    </svg><br/>

    <div class="form">
      width: <input v-model="width" type="range" max="300"><br/>
      height: <input v-model="height" type="range" max="300"><br/>
      x: <input v-model="x" type="range" max="300"><br/>
      y: <input v-model="y" type="range" max="300"><br/>
      rx: <input v-model="rx" type="range" max="150"><br/>
      ry: <input v-model="ry" type="range" max="150"><br/>
      fill: <input v-model="fill" type="color"><br/>
      stroke: <input v-model="stroke_seen" type="checkbox"><br/>
      <div v-if="stroke_seen">
        stroke-width: <input v-model="stroke_width" type="range" max="100"><br/>
        stroke-color: <input v-model="stroke" type="color">
      </div>

      <p>&lt;rect x="{{x}}" y="{{y}}" width="{{width}}" height="{{height}}" rx="{{rx}}" ry="{{ry}}" fill="{{fill}}" <span v-if="stroke_seen">stroke="{{stroke}}" stroke-width:"{{stroke_width}}" </span> /&gt;</p>
    </div>
  </div>
</template>

<script>
  import dragger from './Dragger.vue'

  export default({
    name: 'myrect',
    data () {
      return {
        width: 200,
        height: 100,
        x: 0,
        y: 0,
        rx: 5,
        ry: 5,
        fill: '#BBC42A',
        stroke: '#BBC42A',
        stroke_width: 8,
        stroke_seen: false
      }
    },
    components: {
      dragger
    }
  })
</script>
