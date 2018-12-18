<template>
    <div class="">       
      <p>github input</p>
      <form v-on:submit.prevent="onSubmit">
        <input type="text" v-model="username" placeholder="Enter a github username" />
        <button type="submit">Go!</button>
      </form>
    </div>
</template>

<script>
import { bus } from "../main";

export default {
  name: "GitHubInput",
  components: {},
  data() {
    return {
      username: ""
    };
  },
  mounted() {},
  methods: {
    onSubmit(event) {
      if (this.username && this.username !== "") {
        bus.$emit("new-username", this.username);
      }
    }
  }
};
</script>

<style scoped>
</style>
