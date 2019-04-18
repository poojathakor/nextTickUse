<template>
  <div>
    <div v-if="!editable" class="bg-light p-3">
      <img  v-if="!editable" class="mr-1" src="@/assets/folder.svg"/>
      <input
        :type="editable ? 'hidden' : 'text'"
        v-model="folder.name"
        ref="editFolder"
        :style="editable ? 'border:none;text-align:center' : '' "
        @blur="editable=!editable"
        v-on:keyup.enter="done(folder.name)"
      >
      </div>
      <div v-if="editable" class="d-flex align-items-center">
      	
        <div class="bg-light p-3"
	        @click="makeEdit"
	        style="width:176px;"> 
        	<img
        	class="mr-1"
        	v-if="editable"
        	src="@/assets/folder.svg"
        	/>{{folder.name}}
        </div>
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
         this.$refs.editFolder.select();
      })
    }
  },
  methods: {
    done (name) {
      setTimeout(function(){ alert(` ${name} Folder Created`); }, 500);
      this.editable = true
      this.$emit('createFolder', this.index)
    },
    makeEdit () {
      this.editable = false
      this.$nextTick(() => {
        // console.log(this.$refs.editFolder)
        this.$refs.editFolder.focus();
        this.$refs.editFolder.select();
      })
    }
  }
};
</script>

<style>
</style>
