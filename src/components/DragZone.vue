<template>
  <div
    
    @dragenter.prevent="toggleActive"
    @dragleave.prevent="toggleActive"
    @dragover.prevent
    @drop.prevent="toggleActive"
    :class="{'activeDropZone':active}"
    class="dragzone"
  >
    <span>Drag or Drop files</span>
    <span>OR</span>
    <label for="dragzoneFile">Select file</label>
    <input type="file" id="dragzoneFile" class="dropzoneFile" />
  </div>
</template>

<script>
import {ref} from 'vue'
export default {
  name: "DragZone",
  props: {
    msg: String,
  },
  setup(){
      const active = ref(false);
      const toggleActive = ()=>{
          active.value = !active.value
      };
      return{active, toggleActive}
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.dragzone {
  width: 400px;
  height: 200px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border-radius: 10px;
  border: 2px dashed #41b883;
  background: #fff;
  transition: 0.3s ease all;
  grid-gap: 20px;
}
label {
  padding: 8px 15px;
  color: #fff;
  transition: 0.2s ease all;
  background: #41b883;
}
input {
  display: none;
}
.activeDropZone{
    background: #41b883;
}
.activeDropZone>*{
    color: #fff;
}.activeDropZone>label{
    background: #fff;
    color: #41b882;
}
</style>
