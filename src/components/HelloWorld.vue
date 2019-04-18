<template>
  <div class="container">
    <h1 class="text-center">Add folder</h1>
    <div class="text-right py-3">
      <button @click="addingNewFolder" class="bg-transparent border-0">
        <img src="@/assets/new-folder.svg"/>
      </button>
    </div>
      <div class="row">
        <div class="col-md-3" v-for="(input, ok) in inputs" :key="ok">
          <Folder :folder="input"
          :index="ok"
          @createFolder="FolderCreated"
        />
      </div>
    </div>
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
  methods: {
    addingNewFolder() {
      this.inputs.push({
        name: "New Folder",
        new: true,
        dontshow: false
      });
    },
    FolderCreated(index) {
      console.log(index)
      this.new = false;
    }
  }
};
</script>

<style>
</style>
