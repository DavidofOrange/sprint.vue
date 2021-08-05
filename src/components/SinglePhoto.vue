<template>
  <div class="singlePhotoContainer">
    <img class="single" :src="selectedPhoto" alt="Random Photo" />
  </div>
</template>

<script>
export default {
  name: "SinglePhoto",
  props: ["selectedPhoto"]
};
</script>

<style>
.singlePhotoContainer {
  background-color: rgb(0, 0, 0);
  height: 100%;
}
.single {
  height: auto;
  width: auto;
}
</style>
