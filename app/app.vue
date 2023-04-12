<script></script>

<script>
import { defineNuxtComponent } from "#app";

export default defineNuxtComponent({
  data: () => ({
    photoGallery: [],
  }),
  computed: {
    numberOfPhotos() {
      return this.photoGallery.length;
    },
  },
  methods: {
    fetchPhotoGallery() {
      fetch("https://jsonplaceholder.typicode.com/photos")
        .then((response) => response.json())
        .then((json) => {
          this.photoGallery = json;
        });
    },
  },
});
</script>

<template>
  <h1>Photo Gallery</h1>
  <button @click="fetchPhotoGallery">Fetch!</button>
  <p>{{ numberOfPhotos }} photos</p>
  <ul>
    <li v-for="photo in photoGallery" :key="`photo-id-${photo.id}`">
      <img :src="photo.thumbnailUrl" alt="photo.alt" />
    </li>
  </ul>
</template>

<style></style>
