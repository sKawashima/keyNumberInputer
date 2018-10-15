<template lang='pug'>
v-layout(column='', justify-center='', align-center='')
  v-flex(xs12='', sm8='', md6='')
    p {{tones}}
</template>

<script>
if (process.browser) {
  var Tone = require('tone')
}

var vm

export default {
  data: () => {
    return {
      tones: []
    }
  },
  methods: {
    addInput: (input) => {
      const keys = ['a', 'w', 's', 'e', 'd', 'f', 't', 'g', 'y', 'h', 'u', 'j', 'k', 'o', 'l']
      let r = -1
      keys.forEach((el, i) => {
        if (el === input.key) {
          r = i
          return 0 // out forEach
        }
      })
      if (r !== -1) {
        vm.tones.push(vm.keyboardToFrequency(r))
      }
    },
    keyboardToFrequency: (i) => {
      const frequencys = ['C', 'C#', 'D', 'D#', 'E', 'F', 'F#', 'G', 'G#', 'A', 'A#', 'B', 'C', 'C#', 'D']
      return frequencys[i]
    }
  },
  created () {
    if (process.browser) {
      console.log(Tone.Frequency('A3').toMidi())
      window.addEventListener('keydown', this.addInput, true)
    }
    vm = this
    console.log(this)
  }
}
</script>
