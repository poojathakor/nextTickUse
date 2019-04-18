<template>
  <div class="hello">
    <ul>
      <li
      v-for="(input, index) in inputs"
      :key="`item-${index}`">
       <!--  <input-comp refName="txtEditName" ref="txtEditName" :itemName="input.one" :submitname="submitName"></input-comp>
         -->
         <div v-if="DontshowInput">{{input.one}}</div>
          <input
            :type="DontshowInput ? 'hidden' : 'text'"
            v-model="input.one"
            ref="txtEditName"
            v-on:keyup.enter="submitName"
          />
        <button @click="deleteRow(index)">Delete</button>
      </li>
    </ul>
     <button @click="addRow">Add row</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      inputs: [],
      DontshowInput: false
    }
  },
  methods: {
    addRow () {
      this.inputs.push({
        one: ''
      })
      this.$nextTick(() => {
        this.$refs.txtEditName[0].focus()
      })
    },
    deleteRow(index) {
      this.inputs.splice(index,1)
    },
    submitName () {
      alert('name submitted')
      this.DontshowInput = true
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
