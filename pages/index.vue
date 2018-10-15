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

// var vm = this

export default {
  data: () => {
    return {
      input: 'test'
    }
  },
  methods: {
    addInput: function (input) {
      this.input += input.key
    }
  },
  created () {
    if (process.browser) {
      console.log(Tone.Frequency('A3').toMidi())
      window.addEventListener('keydown', this.addInput, true)
    }
    console.log(this)
  }
}
</script>
