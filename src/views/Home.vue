<template>
  <div class="home">
    <h1>Drop DragZone</h1>
    <DragZone @drop.prevent="drop" @change="selectedFile" msg="Welcome to Your Vue.js App" />
    <span class="file-info">File: {{dropzoneFile.name}}</span>
  </div>
</template>

<script>
// @ is an alias to /src
import DragZone from "@/components/DragZone.vue";
import {ref} from 'vue'
export default {
  name: "Home",
  components: {
    DragZone,
  },
  setup(){
    let dropzoneFile = ref("");
    const drop = (e) => {
      dropzoneFile.value = e.dataTransfer.files[0];
    };
     const selectedFile = () => {
      dropzoneFile.value = document.querySelector(".dropzoneFile").files[0];
    };
    return {dropzoneFile, drop, selectedFile};
  }
};
</script>

<style lang="scss" scoped>
.home{
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
h1, span{
  margin:  20px 0;
}

</style>
