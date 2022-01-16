<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <p> {{ flowers }}</p>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      flowers: [],
      message: "The Flower App",
    };
  },
  created: function () {
    this.indexFlowers();
  },
  methods: {
    indexFlowers: function () {
      axios.get("/flowers").then((response) => {
        console.log("flowers index", response);
        this.flowers = response.data;
      });
    },
  },
};
</script>