<template>
  <div class="nav">
    <img class="vue_logo" alt="Vue logo" src="../assets/logo.png" />
    <h1 class="title" @click="clicked">PHOTO UPLOAD APP</h1>
    <Upload class="upload" />
  </div>
</template>

<script>
import Upload from "./Upload";
/* import { setCurrentView } from "../App"; */

export default {
  name: "Navbar",
  components: {
    Upload
  },

  methods: {
    clicked() {
      this.$emit("title-clicked");
    }
  }
};
</script>

<style>
.nav {
  margin: 0 auto;
  width: 100%;
  height: 400px;
  background-color: maroon;
}
.vue_logo {
  padding-top: 20px;
  height: 150px;
  width: 150px;
}
.upload {
  float: right;
  
}
</style>
