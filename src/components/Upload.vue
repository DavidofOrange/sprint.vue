<template>
  <div>
    <button>Upload</button>
    <input type="file" @change="image_selected" />
  </div>
</template>

<script>
import { saveObject } from "../../utils/index.js";

export default {
  name: "Upload",
  methods: {
    image_selected(e) {
      saveObject(e.target.files[0]);
    }
  }
};
</script>

<style>  
</style>
