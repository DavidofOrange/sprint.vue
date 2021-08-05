<template>
  <div id="app">
    <Navbar @title-clicked="setCurrentViewToAllPhotos" />
    <div v-if="this.currentView === 'AllPhotos'">
      <AllPhotos :photos="photos" @single-photo-data="seeSelectedPhoto" />
    </div>
    <div v-else>
      <SinglePhoto :selectedPhoto="selectedPhoto" />
    </div>
  </div>
</template>

<script>
import Navbar from "./components/Navbar";
import SinglePhoto from "./components/SinglePhoto";
import AllPhotos from "./components/AllPhotos";
import { listObjects, getSingleObject } from "../utils/index.js";

export default {
  name: "App",
  components: {
    Navbar,
    AllPhotos,
    SinglePhoto
  },

  data: function() {
    return {
      currentView: "AllPhotos",
      photos: [],
      selectedPhoto: ""
    };
  },

  async created() {
    const photoObjs = await listObjects(18);
    for (let obj of photoObjs) {
      this.photos.push(await getSingleObject(obj.Key));
    }
  },

  methods: {
    setCurrentViewToAllPhotos() {
      this.currentView = "AllPhotos";
    },

    seeSelectedPhoto(data) {
      this.setSelectedPhoto(data);
      this.currentView = "SinglePhoto";
    },

    setSelectedPhoto(data) {
      this.selectedPhoto = data;
      console.log(this.selectedPhoto);
    }
  }
};
</script>

<style>
#app {
  text-align: center;
  background-color: rgb(0, 0, 0);
  padding: 0;
  margin: 0;
}

.title {
  color: white;
    font-size: 60px;
  text-shadow: black 4px 3px;
  font-family: 'Times New Roman', Times, serif;
}
body {
  margin: 0;
}
</style>
