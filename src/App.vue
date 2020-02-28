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
    <li v-for="(c,i) in colorRange" :key="c+''+i" :style="{'background-color': c}">
      <ul>
        <li v-for="(f,i) in colorRange" :key="'f-'+f+i" :class="{validContrast: validContrast(c,f)}" :style="{'background-color': f, color: c, width: (90/steps - 2) + 'vmin', height: (90/steps - 2) + 'vmin', 'line-height': (90/steps - 2) + 'vmin'}">{{ contrast(c,f) }}</li>
      </ul>
    </li>
  </ul>

  <div class="svg-wrapper">
    <svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 1280 1024" style="enable-background:new 0 0 1280 1024;" xml:space="preserve">
      <g id="Lager_2">
        <rect x="0" y="61" class="st0" width="1280" height="963" />
        <path class="st1" d="M1012,202v823H0V202h25v-33.2c0-1.6,1.3-2.9,2.8-2.9h95.3c1.6,0,2.8,1.3,2.8,2.9V202H1012z" />
        <path class="st2" d="M0,202h25v-33.2c0-1.6,1.3-2.8,2.8-2.8h95.3c1.6,0,2.8,1.3,2.8,2.8V202h886" />
        <rect x="1013" y="61" class="st3" width="267" height="964" />
        <rect x="0" y="3" class="st4" width="1280" height="58" />
        <path class="st5" d="M483,599H37c-2.2,0-4-1.8-4-4V326c0-2.2,1.8-4,4-4h446c2.2,0,4,1.8,4,4v269C487,597.2,485.2,599,483,599z" />
        <path class="st5" d="M974.1,597.5H510.9c-2.4,0-4.4-2-4.4-4.4V283.9c0-2.4,2-4.4,4.4-4.4h463.3c2.4,0,4.4,2,4.4,4.4v309.3C978.5,595.5,976.5,597.5,974.1,597.5z" />
        <g>
          <rect x="45" y="366" class="st1" width="431" height="36" />
          <rect x="45" y="365" class="st3" width="431" height="1" />
          <rect x="45" y="402" class="st3" width="431" height="1" />
          <rect x="45" y="439" class="st3" width="431" height="1" />
          <rect x="45" y="476" class="st3" width="431" height="1" />
          <rect x="45" y="513" class="st3" width="431" height="1" />
          <rect x="45" y="550" class="st3" width="431" height="1" />
          <rect x="45" y="587" class="st3" width="431" height="1" />
          <rect x="45" y="440" class="st1" width="431" height="36" />
          <rect x="45" y="514" class="st1" width="431" height="36" />
        </g>
        <g>
          <rect x="519" y="324" class="st1" width="448" height="36" />
          <rect x="519" y="323" class="st3" width="448" height="1" />
          <rect x="519" y="360" class="st3" width="448" height="1" />
          <rect x="519" y="397" class="st3" width="448" height="1" />
          <rect x="519" y="434" class="st3" width="448" height="1" />
          <rect x="519" y="471" class="st3" width="448" height="1" />
          <rect x="519" y="508" class="st3" width="448" height="1" />
          <rect x="519" y="545" class="st3" width="448" height="1" />
          <rect x="519" y="398" class="st1" width="448" height="36" />
          <rect x="519" y="472" class="st1" width="448" height="36" />
          <rect x="519" y="582" class="st3" width="448" height="1" />
          <rect x="519" y="546" class="st1" width="448" height="36" />
        </g>
        <text transform="matrix(1 0 0 1 52.0967 353.7856)" class="st6 st7 st8">SKOLA</text>
        <text transform="matrix(1 0 0 1 249.0967 353.7856)" class="st6 st7 st8">ANTAL ELEVER</text>
        <text transform="matrix(1 0 0 1 526.0967 311.7856)" class="st6 st7 st8">NAMN</text>
        <text transform="matrix(1 0 0 1 710.0967 311.7856)" class="st6 st7 st8">SENASTE BESÖK</text>
      </g>
      <g id="Lager_3">
        <text transform="matrix(1 0 0 1 23.0967 107.7856)" class="st9 st7 st10">Hemsidan</text>
        <text transform="matrix(1 0 0 1 27.0967 257.7856)" class="st9 st7 st11">Dina utvalda</text>
        <text transform="matrix(1 0 0 1 507.0967 257.7856)" class="st9 st7 st11">Dina senaste elever</text>
        <text transform="matrix(1 0 0 1 507.0967 733.7856)" class="st9 st7 st11">Dina bevakningar</text>
        <text transform="matrix(1 0 0 1 29.0967 664.7856)" class="st9 st7 st11">Dina länkar</text>
        <text transform="matrix(1 0 0 1 23.0967 133.7856)" class="st9 st12 st13">Välkommen Alfred!</text>
        <text transform="matrix(1 0 0 1 161.0967 187.7856)" class="st9 st12 st14">Signeringskorg</text>
        <text transform="matrix(1 0 0 1 59.0967 187.7856)" class="st9 st12 st14">Din sida</text>
        <text transform="matrix(1 0 0 1 55.0967 388.7856)">
          <tspan x="0" y="0" class="st9 st12 st8">Jockeskolan</tspan>
          <tspan x="0" y="37" class="st9 st12 st8">Livets Hårda Förskola</tspan>
          <tspan x="0" y="74" class="st9 st12 st8">Livets hårda skola</tspan>
          <tspan x="0" y="111" class="st9 st12 st8">Maleficarum</tspan>
          <tspan x="0" y="148" class="st9 st12 st8">Skolan för pedagogik</tspan>
          <tspan x="0" y="185" class="st9 st12 st8">Testskolan</tspan>
        </text>
        <text transform="matrix(1 0 0 1 254.0967 388.7856)">
          <tspan x="0" y="0" class="st9 st12 st8">69</tspan>
          <tspan x="0" y="37" class="st9 st12 st8">1</tspan>
          <tspan x="0" y="74" class="st9 st12 st8">73</tspan>
          <tspan x="0" y="111" class="st9 st12 st8">55</tspan>
          <tspan x="0" y="148" class="st9 st12 st8">46</tspan>
          <tspan x="0" y="185" class="st9 st12 st8">44</tspan>
        </text>
        <text transform="matrix(1 0 0 1 529.0967 344.7856)">
          <tspan x="0" y="0" class="st9 st12 st8">SF (860304)</tspan>
          <tspan x="0" y="37" class="st9 st12 st8">JA (770503)</tspan>
          <tspan x="0" y="74" class="st9 st12 st8">JA (770403)</tspan>
          <tspan x="0" y="111" class="st9 st12 st8">JA (770403)</tspan>
          <tspan x="0" y="148" class="st9 st12 st8">MH (091203)</tspan>
          <tspan x="0" y="185" class="st9 st12 st8">TL (090211)</tspan>
          <tspan x="0" y="222" class="st9 st12 st8">EE (090612)</tspan>
        </text>
        <text transform="matrix(1 0 0 1 714.0967 344.7856)">
          <tspan x="0" y="0" class="st9 st12 st8">för 30 min sedan</tspan>
          <tspan x="0" y="37" class="st9 st12 st8">för 45 min sedan</tspan>
          <tspan x="0" y="74" class="st9 st12 st8">för 1 timme sedan</tspan>
          <tspan x="0" y="111" class="st9 st12 st8">för 2 timmar sedan</tspan>
          <tspan x="0" y="148" class="st9 st12 st8">för 2 timmar sedan</tspan>
          <tspan x="0" y="185" class="st9 st12 st8">för 14 dagar sedan</tspan>
          <tspan x="0" y="222" class="st9 st12 st8">för 15 dagar sedan</tspan>
        </text>
        <text transform="matrix(1 0 0 1 310.0967 187.7856)" class="st9 st12 st14">Inställningar</text>
        <text transform="matrix(1 0 0 1 443.0967 187.7856)" class="st9 st12 st14">Om Prorenata Journal</text>
        <rect class="st15" width="1280" height="3" />
      </g>
    </svg>
  </div>

  <div class="code">
    <div>
      <div v-for="(color, index) in colorRange" :key="index">@color-s{{colorRange.length-index}}00: {{color}};</div>
    </div>
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
      color1: '#F5FDFF',
      color2: '#00303C',
      mode: 'lab',
      gamma: '1.25',
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
      return Math.round(chroma.contrast(c1, c2) * 100) / 100
    },
    validContrast(c1, c2) {
      return (chroma.contrast(c1, c2) < this.contrastThreshold)
    }
  },
  watch: {
    colorRange() {
      this.colorRange.forEach((color,index) => {
        document.documentElement.style.setProperty(`--s${(index+1)}00`, color);
      })
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
        } catch (e) {
          this.validJson = false
        }
        if (newValueParsed) {
          this.color1 = newValueParsed.color1
          this.color2 = newValueParsed.color2
          this.mode = newValueParsed.mode
          this.gamma = newValueParsed.gamma
          this.steps = newValueParsed.steps
          this.contrastThreshold = newValueParsed.contrastThreshold
          this.validJson = true
        }
      }
    }
  }
}
</script>

<style>
body,
html {
  margin: 0;
  padding: 0;
  background: #888;
}

input,
select {
  padding: 4px;
  margin: 6px;
  border-radius: 4px;
  border: 1px solid #DDD;
}

input.error {
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

#app>ul {
  display: inline-block;
  margin: 5vmin auto;
}

#app>ul li {
  display: block;
}

#app>ul li li {
  margin: 1vmin;
  display: inline-block;
  border-radius: 999999px;
  font: 400 1rem sans-serif;
}

#app>ul:hover li li.validContrast {
  opacity: 0;
}

.svg-wrapper > svg {
  max-width: 1280px;
  height: auto;
  margin: 0 auto;
}

.settings {
  position: fixed;
  top: 0;
  right: 0;
  left: 0px;
  background: rgba(0, 0, 0, 0.2);
  padding: 4px;
}

.settings>* {
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

.code>* {
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
  background: #F2F2F2;
}



/* SVG */

:root{
  --s100: #EFF2F3;
  --s200: #E5EBEE;
  --s400: #96A9AD;
  --s500: #859BA0;
  --s700: #657D82;
  --s800: #586C71;
}


  .st0 {
    fill: var(--s100);
  }

  .st1 {
    fill: var(--s200);
  }

  .st2 {
    fill: none;
    stroke: var(--s500);
    stroke-miterlimit: 10;
  }

  .st3 {
    fill: var(--s400);
  }

  .st4 {
    fill: var(--s700);
  }

  .st5 {
    fill: var(--s100);
    stroke: #FFFFFF;
    stroke-miterlimit: 10;
  }

  .st6 {
    fill: var(--s800);
  }

  .st7 {
    font-family: 'InterUI-SemiBold';
  }

  .st8 {
    font-size: 12px;
  }

  .st9 {
    fill: #363027;
  }

  .st10 {
    font-size: 32px;
  }

  .st11 {
    font-size: 27px;
  }

  .st12 {
    font-family: 'InterUI-Medium';
  }

  .st13 {
    font-size: 16px;
  }

  .st14 {
    font-size: 14px;
  }

  .st15 {
    fill: #F6A700;
  }

</style>
