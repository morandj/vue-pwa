<template>
  <div class="test-axios">
    <h1>Test Axios</h1>
    <h2 v-text="io"></h2>
    <img id="img" v-bind:src="image">
    <h3>{{ message }}</h3>
    <button v-on:click="refresh">Refresh</button>

    <hr>
    <input type="text" v-model="io">
    <p>{{ io }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "TestAxios",
  data() {
    return {
      image: "x",
      message: "a little message",
      io: "placeholder"
    };
  },
  methods: {
    getImage() {
      axios
        .get("https://dog.ceo/api/breeds/image/random")
        .then(response => {
          this.image = response.data.message;
          console.log(response);
        })
        .catch(error => {
          console.log(error);
        });
    },
    refresh() {
      this.message = this.io;
      this.getImage();
    }
  },
  components: {},
  props: {},
  created() {
    this.getImage();
  }
};
</script>

<style scoped>
#img {
  height: 200px;
  widows: 200px;
}
</style>
