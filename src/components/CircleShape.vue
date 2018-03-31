<template>
  <svg></svg>
</template>

<script>
  import * as d3 from 'd3'

  export default {
    name: 'CircleShape',
    props: ['option', 'string'],
    data () {
      return {
        opt: {
          width: 700,   // svg width
          height: 500,  // svg height
          x: 350,       // shape x position
          y: 250,       // shape r position
          r: 150,       // circle radius
          bg: '#ff0000'    // shape background
        }
      }
    },
    watch: {
      string () {
        this.clear()
        this.drawCircle()
      }
    },
    mounted () {
      this.setOptions(this.option)
      this.drawCircle()
    },
    methods: {
      setOptions (option) {
        this.opt = Object.assign({}, this.opt, option)
      },
      drawCircle () {
        const opt = this.opt
        const svg = d3.select(this.$el)
          .attr('width', opt.width)
          .attr('height', opt.height)
        const g = svg.append('g')
          .attr('transform', `translate(${opt.x},${opt.y})`)
        g.append('circle')
          .attr('r', opt.r)
          .attr('stroke', 'black')
          .attr('fill', opt.bg)
        g.append('text')
          .attr('style', 'text-anchor: middle')
          .text(this.string)
      },
      clear () {
        d3.select(this.$el).selectAll('g').remove()
      }
    }
  }
</script>

<style scoped>
  svg {
    border: 1px solid;
  }
</style>
