<template>
  <div>
    <input id="datepicker" type="text" :value="value">
  </div>
</template>

<script>
import 'pikaday/css/pikaday.css'
export default {
  name: "Pikaday",
  props: {
    value: {
      type: String
    }
  },
  mounted() {
    if(process.client) {
      const ctx = this
      const Pikaday = require('pikaday')
      new Pikaday({
        field: document.getElementById('datepicker'),
        onSelect: function (value) {
          ctx.$emit('input', value.toString())
          // console.log(Pikaday.toString())
        }
      })
    }
      // new Pikaday({
      //   field: document.getElementById('datepicker')
      // })
  }
}
</script>
