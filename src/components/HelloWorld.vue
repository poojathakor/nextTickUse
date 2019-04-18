<template>
  <div class="hello">
    <ul>
      <li
      v-for="(input, index) in inputs"
      :key="`item-${index}`">
        <input-comp refName="txtEditName" ref="txtEditName" :itemName="input.one" :submitname="submitName"></input-comp>
        
        <button @click="deleteRow(index)">Delete</button>
      </li>
    </ul>
     <button @click="addRow">Add row</button>
  </div>
</template>

<script>
import Vue from 'vue'
import inputComp from './inputComp.vue'
export default {
  name: 'HelloWorld',
  components: {
    'input-comp': inputComp
  },
  data() {
    return {
      inputs: []
    }
  },
  methods: {
    addRow () {
      this.inputs.push({
        one: ''
      })
      this.$nextTick(() => {
        this.$refs.txtEditName.focus()
      })
    },
    deleteRow(index) {
      this.inputs.splice(index,1)
    },
    submitName () {
      alert('name submitted')
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
