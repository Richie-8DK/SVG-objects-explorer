<template>
  <div>
    <svg id="svg" width="300" height="300">
      <polyline
      :points="points_1d"
      :stroke="stroke"
      :stroke-width="stroke_width"
      :fill="fill_seen ? fill : 'none'" />
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
      stroke-width: <input v-model.number="stroke_width" type="range" max="100"><br/>
      stroke: <input v-model="stroke" type="color"><br/>
      fill: <input v-model="fill_seen" type="checkbox"><br/>
      <div v-if="fill_seen">
        fill-color: <input v-model="fill" type="color"><br/>
      </div>

      <p>&lt;polyline points="{{points_1d}}" stroke="{{stroke}}" stroke-width:"{{stroke_width}}" <span v-if="fill_seen">fill="{{fill}}"</span> /&gt;</p>
    </div>
  </div>
</template>

<script>
  import dragger from './Dragger.vue'

  export default({
    name: 'mypolyline',
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
        fill_seen: false
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
