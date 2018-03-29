<template>
  <address-picker v-model="value"></address-picker>
</template>
<script>
import addressPicker from './addressPicker/addressPicker.vue'
export default {
  components: {
    "address-picker": addressPicker
  },
  data () {
    return {
      value: []
    }
  }
}
</script>
<style>

</style>
