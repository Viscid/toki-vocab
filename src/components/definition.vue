<template>
  <div id="definition" v-bind:style="{ left: (x + 15) + 'px', top: (y + 15) + 'px' }" v-if="word">
    <h2> {{ word.word }} </h2>
    <ul>
      <li v-for="definition in word.definitions">
        <h3> {{ definition.category }} </h3>
        <p> {{ definition.definition }} </p>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'definition',
  props: ['word', 'mousePos'],
  data () {
    return {
      x: 0,
      y: 0
    }
  },
  watch: {
    'mousePos': function (val) {
      this.x = val.x
      this.y = val.y
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#definition {
  text-align: left;
  position: absolute;
  background-color: #FFF;
  padding: 0 0.5em;
  margin: 0;
  border: 2px solid black;
  width: 500px;
}

ul {
  list-style: none;
}

h2 {
  margin: 0.5em 0 0 0;
  padding-bottom: 0.25em;
  border-bottom: 1px solid #CCC;
}

p {
  display: inline;
  font-style: italic;
}

h3 {
  display: inline-block;
  padding-right: 0 1em 0 0;
  margin: 0.5em 0.5em 0 0;
}

</style>
