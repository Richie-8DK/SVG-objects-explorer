<template>
  <circle
  :cx="x"
  :cy="y"
  r="5"
  fill="red"
  @mousedown="start_drag"
  @mouseup="cancel_drag"/>
</template>
<script>
  export default {
    props: ['x', 'y'],
    data () {
      return {
        dragged: false
      }
    },
    methods: {
      start_drag(event) {
        this.dragged = true
        event.preventDefault()
      },
      cancel_drag() {
        this.dragged = false
      }
    },
    mounted: function() {
      // TODO: this is an entire parent, not just the svg
      // should be svg
      const parent = this.$parent.$el

      parent.addEventListener('mousemove', event => {
        let {left, top} = this.$parent.$el.getBoundingClientRect()
        let {clientX, clientY} = event

        this.$emit('update:x', this.dragged ? clientX - left : this.x)
        this.$emit('update:y', this.dragged ? clientY - top : this.y)
      })

      parent.addEventListener('mouseleave', this.cancel_drag)
      parent.addEventListener('mouseup', this.cancel_drag)
    }
  }
</script>
