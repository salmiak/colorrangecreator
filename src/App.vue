<template>
  <div id="app">
    <div class="settings">
      <input v-model="color1" title="color 1" :class="{error: !isValid(color1)}" />
      <input v-model="color2" title="color 2" :class="{error: !isValid(color2)}" />
      <select v-model="mode" title="mode">
        <option value="">rgb</option>
        <option>lrgb</option>
        <option>lab</option>
        <option>hsl</option>
        <option>lch</option>
      </select>
      <input v-model="gamma" type="number" step="0.05" title="gamma" />
      <select v-model="contrastThreshold" title="contrast validation level">
        <option value="3">AA Large (3:1)</option>
        <option value="4.5">AA (4.5:1)</option>
        <option value="7">AAA (7:1)</option>
      </select>
      <input v-model="steps" type="number" step="1" title="steps" />
    </div>

    <ul>
      <li v-for="c in colorRange" :key="c" :style="{'background-color': c}">
        <ul>
          <li v-for="f in colorRange" :key="'f-'+f" :class="{validContrast: validContrast(c,f)}" :style="{'background-color': f, color: c, width: (90/steps - 4) + 'vmin', height: (90/steps - 4) + 'vmin', 'line-height': (90/steps - 4) + 'vmin'}">{{ contrast(c,f) }}</li>
        </ul>
      </li>
    </ul>

    <div class="code">
      <div><div v-for="(color, index) in colorRange" :key="index">@color-s{{colorRange.length-index}}00: {{color}};</div></div>
      <textarea v-model="dataAsJSON" :class="{'is-valid': validJson}"></textarea>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import chroma from 'chroma-js'

export default {
  name: 'app',
  data() {
    return {
      color1: '#00303C',
      color2: '#F7FFF7',
      mode: 'lab',
      gamma: '0.75',
      steps: 10,
      contrastThreshold: 3,
      validJson: true
    }
  },
  components: {
    // HelloWorld
  },
  methods: {
    isValid(color) {
      return chroma.valid(color)
    },
    contrast(c1, c2) {
      return Math.round(chroma.contrast(c1, c2)*100)/100
    },
    validContrast(c1,c2) {
      return (chroma.contrast(c1, c2) < this.contrastThreshold)
    }
  },
  computed: {
    colorRange() {
      if (!chroma.valid(this.color1) || !chroma.valid(this.color2))
        return ['black']

      var cObj = chroma.scale([chroma(this.color1), chroma(this.color2)]).mode(this.mode)

      if (this.gamma) {
        cObj.gamma(this.gamma)
      } else {
        cObj.correctLightness()
      }
      return cObj.colors(this.steps)
    },
    dataAsJSON: {
      get: function() {
        return JSON.stringify({
          color1: this.color1,
          color2: this.color2,
          mode: this.mode,
          gamma: this.gamma,
          steps: this.steps,
          contrastThreshold: this.contrastThreshold
        }, undefined, 2)
      },
      set(newValue) {
        var newValueParsed = undefined
        try {
          newValueParsed = JSON.parse(newValue)
        } catch(e) {
          this.validJson = false
        }
        if (newValueParsed) {
          this.color1 =  newValueParsed.color1
          this.color2 =  newValueParsed.color2
          this.mode =  newValueParsed.mode
          this.gamma =  newValueParsed.gamma
          this.steps =  newValueParsed.steps
          this.contrastThreshold =  newValueParsed.contrastThreshold
          this.validJson = true
        }
      }
    }
  }
}
</script>

<style>
body, html {
  margin: 0;
  padding: 0;
  background: #888;
}
input, select {
  padding: 4px;
  margin: 6px;
  border-radius: 4px;
  border: 1px solid #DDD;
}
input.error{
  border-color: red;
}
ul {
  margin: 0;
  padding: 0;
  font-size: 0;
  line-height: 0;
}
#app {
  padding-top: 30px;
  text-align: center;
}
#app > ul {
  display: inline-block;
  margin: 5vmin auto;
}
#app > ul li {
  display: block;
}
#app > ul li li {
  margin: 2vmin;
  display: inline-block;
  border-radius: 999999px;
  font: 300 1rem sans-serif;
}
#app > ul:hover li li.validContrast {
  opacity: 0;
}
.settings {
  position: fixed;
  top: 0;
  right: 0;
  left: 0px;
  background: rgba(0,0,0,0.2);
  padding: 4px;
}
.settings > * {
  display: inline-block;
}
.code {
  font-family: monospace;
  text-align: left;
  background: #fff;
  color: #222;
  padding: 0px;
  margin-top: 80px;
  display: flex;
  align-content: stretch;
  justify-content: space-between;
}
.code > * {
  width: 50%;
  font-family: inherit;
  font-size: inherit;
  margin: 0;
  border: 0;
  padding: .75rem;
}
.code textarea {
  background: pink;
}
.code textarea.is-valid {
  background:  #F2F2F2;
}
</style>
