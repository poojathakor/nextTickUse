<template>
  <div>
    <div>
      <input
        :type="editable ? 'hidden' : 'text'"
        v-model="folder.name"
        ref="editFolder"
        :style="editable ? 'border:none;text-align:center' : '' "
        
        v-on:keyup.enter="done"
      >
      </div>
      <div v-if="editable">
        <div style="background:silver;width:200px;" @click="makeEdit"> {{folder.name}}</div>
      </div>
  </div>
</template>

<script>
export default {
  props: {
    folder:{
      type: Object
    },
    index: {
      type: Number
    }
  },
  data () {
    return {
      editable: this.folder.dontShow
    }
  },
  mounted () {
    if (this.folder.new) {
      this.$nextTick(() => {
        // console.log(this.$refs.editFolder)
        this.$refs.editFolder.focus();
      })
    }
  },
  methods: {
    done () {
      setTimeout(function(){ alert("Folder Created"); }, 2000);
      this.editable = true
      this.$emit('createFolder', this.index)
    },
    makeEdit () {
      this.editable = false
      this.$nextTick(() => {
        // console.log(this.$refs.editFolder)
        this.$refs.editFolder.focus();
      })
    }
  }
};
</script>

<style>
</style>
