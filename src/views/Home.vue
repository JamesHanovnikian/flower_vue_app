<template>
  <div class="home">
    <div class="container">
        <h1>{{ message }}</h1>
      <div class="flex-container">
        <div v-for="flower in flowers" class="card" style="width: 18rem;">
        <img class="card-img-top" v-bind:src="flower.image" alt="Card image cap">
        <div class="card-body">
        <h5 class="card-title"> {{ flower.name }}</h5>
      </div>
        <ul class="list-group list-group-flush">
          <li class="list-group-item"> Family: {{ flower.family }}</li>
          <li class="list-group-item"> Predominant Color: {{ flower.color }}</li>
        </ul>
      </div>

      </div>
      
    </div>
  </div>
</template>

<style>
img {
  max-width: 180px;
  max-height: 100px;
}

.flex-container {
  display: flex;
  justify-content: space-around;
}

.flex-container .card {
}

h1 {
  padding-bottom: 45px;
}
</style>

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