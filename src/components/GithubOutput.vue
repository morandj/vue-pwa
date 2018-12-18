<template>
  <div>
    <p v-if="currentUsername == null">
    Enter a username above to see their Github data
    </p>
    <p v-else>
    Below are the results for {{ currentUsername }}
    </p>
    <div v-if="githubData[currentUsername]">
      <h4>{{ githubData[currentUsername].name }}</h4>
      <p>{{ githubData[currentUsername].company }}</p>
      <p>Number of repos: {{ githubData[currentUsername].public_repos }}</p>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import { bus } from "../main";

export default {
  name: "GitHubOutput",
  components: {
    bus
  },
  data() {
    return {
      currentUsername: "null",
      githubData: {}
    };
  },

  created() {
    bus.$on("new-username", this.onUsernameChange);
  },
  destroyed() {
    bus.$off("new-username", this.onUsernameChange);
  },
  mounted() {},
  methods: {
    onUsernameChange(name) {
      this.currentUsername = name;
      this.fetchGithubData(name);
    },

    fetchGithubData(name) {
      // if we have data already, don't request again
      if (this.githubData.hasOwnProperty(name)) return;

      const url = `https://api.github.com/users/${name}`;
      fetch(url)
        .then(r => r.json())
        .then(data => {
          // in here we need to update the githubData object
          console.log("data:", data);
          Vue.set(this.githubData, name, data);
        });
    }
  }
};
</script>

<style scoped>
</style>
