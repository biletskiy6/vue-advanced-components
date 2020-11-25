<template>
  <div class="max-w-sm mx-auto">
    <div class="card">
      <label for="" class="block">
        <span class="form-label">Select a date</span>
        <input id="datepicker" type="text" class="form-input" />
      </label>
    </div>
  </div>
</template>

<script>
  import Vue from 'vue';
  if (process.browser) {
    Vue.use(require('Pikaday'))
  }

export default {
  name: "DatePicker",
  mounted() {
    // const picker = new Pikday({
    //   field: document.getElementById('datepicker')
    // });
  },
};
</script>
