<template>
    <div class="test-one"> 
      <p>Hello</p>
      <github-input />
      <github-output />
    </div>
</template>

<script>
import GithubInput from "./GithubInput.vue";
import GithubOutput from "./GithubOutput.vue";
export default {
  name: "TestOne",
  components: {
    GithubInput,
    GithubOutput
  },
  data() {
    return {};
  },
  mounted() {},
  methods: {}
};
</script>

<style scoped>
</style>
