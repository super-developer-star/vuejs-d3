<template>
  <svg width="600" height="400"></svg>
</template>

<script>
  import * as d3 from 'd3'

  export default {
    name: 'CircleShape2',
    props: ['option', 'string'],
    data () {
      return {
        opt: {
          x: 400,         // shape y position
          y: 200,         // shape x position
          bg: '#00ff00',  // shape background
          r: 150          // circle radius
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
        const that = this
        this.options = option.map(opt => Object.assign({}, that.opt, opt))
      },
      drawCircle () {
        const svg = d3.select(this.$el)
        const g = svg.selectAll('g')
          .data(this.options)
          .enter()
          .append('g')
          .attr('transform', d => `translate(${d.x},${d.y})`)

        g.append('circle')
          .attr('r', d => d.r)
          .attr('stroke', 'black')
          .attr('fill', d => d.bg)

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
