<template>
  <div>

  <input
    type="text"
    v-model="itemName"
    :ref="refName"
    v-on:keyup.enter="submitname"
  />
  

</div>
</template>
<script>
export default {
  props: ['itemName','refName'],
  methods: {
    submitName () {
      this.$emit('submitname')
    }
  }
}
</script>