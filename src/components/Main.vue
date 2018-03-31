<template>
  <div class='main'>
    <h1>{{ msg }}</h1>
    <input v-model='text' placeholder='Please Enter.'>
    <h3>Example 1(Draw shapes on every svg by data</h3>
    <CircleShape :option='option1' :string="text"></CircleShape>
    <CircleShape :option='option2' :string="text"></CircleShape>

    <h3>Example 2(Draw shapes on only 1 svg by data</h3>
    <CircleShape2 :option='option3' :string="text"></CircleShape2>
  </div>
</template>

<script>
  import CircleShape from './CircleShape'
  import CircleShape2 from './CircleShape2'

  export default {
    name: 'Main',
    components: {
      CircleShape,
      CircleShape2
    },
    data () {
      return {
        msg: 'Welcome to Your Vue.js + D3.js Test App',
        text: null,
        option1: {
          width: 300,   // svg width
          height: 400,  // svg height
          x: 150,       // shape x position
          y: 150,       // shape r position
          r: 100,       // circle radius
          bg: '#f0f'    // shape background
        },
        option2: {},
        option3: [
          {
            bg: '#0ff'
          },
          {
            x: 120,
            y: 250,
            r: 100
          }
        ]
      }
    }
  }
</script>

<!-- Add 'scoped' attribute to limit CSS to this component only -->
<style scoped>
  h1, h2 {
    font-weight: normal;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }

  a {
    color: #42b983;
  }
</style>
