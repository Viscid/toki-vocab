<template>
  <div id="vocab-list" @mousemove="handleMouseMove">

    <h1> Toki Pona Words </h1>
    <ul>
      <span v-for="(definitions, word) in words">
        <br v-show="definitions[0]['alphaBreak']" />
        <li
          :key="word"
          @mouseover="handleMouseOver(word, definitions)"
          @mouseleave="handleMouseLeave">
            {{ word }}
        </li>
      </span>
    </ul>

    <definition :mousePos="mousePos" :v-if="activeWord" :word="activeWord"></definition>

  </div>
</template>

<script>
import dictionary from '../assets/toki-pona-dictionary.json'
import word from '../components/word'
import definition from '../components/definition'

export default {
  name: 'vocab-list',
  components: { word, definition },
  data () {
    return {
      words: dictionary,
      activeWord: null,
      mousePos: {x: 0, y: 0}
    }
  },
  methods: {
    handleMouseOver: function (word, definitions) {
      this.activeWord = { word, definitions }
    },
    handleMouseLeave: function () {
      this.activeWord = undefined
    },
    handleMouseMove: function (e) {
      this.mousePos = {x: e.clientX, y: e.clientY}
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#vocab-list {
  margin: 0 auto;
  text-align: left;
}

h1 {
  text-align: center;
}

ul {
  list-style: none;
  padding-left: 0;
}

li {
    display: inline-block;
    font-size: 1.1em;
    padding: 0.35em;
    border: 1px solid #CCC;
    margin: 0.25em;
    box-shadow: 2px 2px #AAA;
    cursor: pointer;
}

li:hover {
  background-color: #EEE;
}

.alphaBreak {
  clear: right;
}


</style>
