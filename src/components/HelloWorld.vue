<template>
  <div>
    <h1>Home</h1>
    <div v-for="(input, ok) in inputs" :key="ok">
      <Folder :folder="input"
      :index="ok"
      @createFolder="FolderCreated"
    />
    </div>
    <button @click="addingNewFolder">Add Folder</button>
  </div>
</template>

<script>
import Folder from "@/components/Folder";
export default {
  components: {
    Folder
  },
  data() {
    return {
      inputs: [],
    };
  },
  // directives: {
  //   focus: {
  //     // directive definition
  //     inserted: function (el) {
  //       el.focus()
  //     }
  //   }
  // },
  methods: {
    addingNewFolder() {
      this.inputs.push({
        name: "New Folder",
        new: true,
        dontshow: false
      });
    },
    FolderCreated(index) {
      console.log(index);
      this.new = false;
    }
  }
};
</script>

<style>
</style>
