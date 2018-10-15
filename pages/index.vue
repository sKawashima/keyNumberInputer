<template lang='pug'>
v-layout(column='', justify-center='', align-center='')
  v-flex(xs12='', sm8='', md6='')
    p {{input}}
</template>

<script>
// import Logo from '~/components/Logo.vue'
// import VuetifyLogo from '~/components/VuetifyLogo.vue'
if (process.browser) {
  var Tone = require('tone')
}

var vm = this

export default {
  data: () => {
    return {
      input: 'test'
    }
  },
  methods: {
    addInput: (input) => {
      console.log(input.key)
      // vm.data.input += input.key
      console.log(vm)
    }
  },
  mounted () {
    if (process.browser) {
      console.log(Tone.Frequency('A3').toMidi())
      window.addEventListener('keydown', this.addInput)
    }
  }
}
</script>
