<template>
  <div>
    <svg id="svg" width="300" height="300">
      <polygon
      :points="points_1d"
      :stroke="stroke_seen ? stroke : ''"
      :stroke-width="stroke_seen ? stroke_width : ''"
      :fill="fill" />
      <dragger
      v-for="(point, index) in points"
      :key="index"
      :x.sync="point.x"
      :y.sync="point.y"/>
    </svg><br/>

    <div class="form">
      points: <div v-for="(point, index) in points" :key="index">
        x: <input v-model.number="point.x" type="range" max="300">
        y: <input v-model.number="point.y" type="range" max="300">
        <button @click="points.splice(index, 1)">delete</button><br/>
      </div>
      <button @click="points.push({ x: 0, y: 0 })">add</button><br/>
      fill: <input v-model="fill" type="color"><br/>
      stroke: <input v-model="stroke_seen" type="checkbox"><br/>
      <div v-if="stroke_seen">
        stroke-width: <input v-model.number="stroke_width" type="range" max="100"><br/>
        stroke-color: <input v-model="stroke" type="color">
      </div>

      <p>&lt;polygon points="{{points_1d}}" fill="{{fill}}" <span v-if="stroke_seen">stroke="{{stroke}}" stroke-width="{{stroke_width}}"</span> /&gt;</p>
    </div>
  </div>
</template>

<script>
  import dragger from './Dragger.vue'

  export default({
    name: 'mypolygon',
    data () {
      return {
        points: [
        { x: 0, y: 40 },
        { x: 40, y: 40 },
        { x: 40, y: 80 },
        { x: 80, y: 80 },
        { x: 80, y: 120 },
        { x: 120, y: 120 },
        { x: 120, y: 160 }],
        fill: '#BBC42A',
        stroke: '#BBC42A',
        stroke_width: 8,
        stroke_seen: false
      }
    },
    computed: {
      points_1d: function () {
        return this.points.reduce((points_1d, point) =>
          `${points_1d} ${point.x},${point.y}`, '')
      }
    },
    components: {
      dragger
    }
  })
</script>
