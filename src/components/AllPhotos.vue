<template>
  <div class="allPhotosContainer">
    <img
      v-for="base64string of photos"
      :key="base64string"
      :src="`data:image/png;base64,${base64string}`"
      alt="obj"
      class="all-photos-photo"
      @click="photoData(`data:image/png;base64,${base64string}`)"
    />
  </div>
</template>

<script>
export default {
  name: "AllPhotos",
  props: ["photos"] /* {
    photos: {
      type: Array,
    },
  }, */,
  methods: {
    photoData(data) {
      this.$emit("single-photo-data", data);
    }
  }
};
</script>

<style>
.allPhotosContainer {
  background-color: white;
  border: 2px solid black;
  padding: 10px;
  margin: 5px auto;
  display: grid;
  grid-auto-flow: 300px 300px 300px;
  grid-template-columns: 300px 300px 300px;
  grid-gap: 10px;
  width: 920px;
}

.all-photos-photo {
  border: 1px solid black;
  display: inline;
  margin: 0 auto;
  height: 300px;
  width: 300px;
  cursor: pointer;
}
</style>
