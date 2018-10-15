<template lang='pug'>
v-layout(column='', justify-center='', align-center='')
  v-flex(xs12='', sm8='', md6='')
    p {{input}}
</template>

<script>
if (process.browser) {
  var Tone = require('tone')
}

var vm

export default {
  data: () => {
    return {
      input: 'test'
    }
  },
  methods: {
    addInput: (input) => {
      vm.input += input.key
      console.log(vm.keyboardToFrequency(input.key))
    },
    keyboardToFrequency: (input) => {
      console.log('keyboardToFrequency')
      const frequencys = ['C', 'D', 'E', 'F', 'G', 'A', 'B', 'C', 'D']
      const keys = ['a', 's', 'd', 'f', 'g', 'h', 'j', 'k', 'l']
      let r
      keys.forEach((el, i) => {
        if (el === input) {
          console.log(frequencys[i])
          r = frequencys[i]
          return 0 // out forEach
        }
      })
      return r
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
