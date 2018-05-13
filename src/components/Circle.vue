<template>
  <div>
    <svg id="svg" width="300" height="300">
      <circle
      :stroke="stroke_seen ? stroke : ''"
      :stroke-width="stroke_seen ? stroke_width : ''"
      :cx="cx"
      :cy="cy"
      :r="r"
      :fill="fill" />
    </svg><br/>

    <div class="form">
      r: <input v-model="r" type="range" max="150"><br/>
      cx: <input v-model="cx" type="range" max="300"><br/>
      cy: <input v-model="cy" type="range" max="300"><br/>
      fill: <input v-model="fill" type="color"><br/>
      stroke: <input v-model="stroke_seen" type="checkbox"><br/>
      <div v-if="stroke_seen">
        stroke-width: <input v-model="stroke_width" type="range" max="100"><br/>
        stroke-color: <input v-model="stroke" type="color">
      </div>

      <p>&lt;circle r="{{r}}" cx="{{cx}}" cx="{{cx}}" fill="{{fill}}" <span v-if="stroke_seen">stroke="{{stroke}}" stroke-width:"{{stroke_width}}"</span> /&gt;</p>
    </div>
  </div>
</template>

<script>
  export default({
    name: 'mycircle',
    data () {
      return {
        r: 100,
        cx: 160,
        cy: 140,
        fill: '#BBC42A',
        stroke: '#BBC42A',
        stroke_width: 8,
        stroke_seen: false
      }
    }
  })
</script>