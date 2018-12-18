<template>
  <div class="news-api">
    <h1>News API</h1>
    <hr>
    <img src="../assets/logo.png">
    <img src="../assets/logo.png">
    
    <hr>
    <ul>
      <li v-for="source in sources" v-bind:key="source.id">{{ source.name }}</li>
    </ul>
    <button>Settings</button>
    <form>
      <label>Sources</label>
      <select v-model="selectedSource">
        <option v-for="source in sources" v-bind:key="source.id">{{ source.name }}</option>
      </select>
      <span>Selected: {{ selectedSource }}</span>
    </form>
    <!-- <img v-bind:src="message"/> -->
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "NewsApi",
  data() {
    return {
      sources: [
        {
          id: "",
          name: ""
        }
      ],
      selectedSource: "",
      language: "en",
      choice: {
        languages: ["de", "en", "es", "fr", "it"],
        domains: []
      },
      baseUrl: "https://newsapi.org/v2/",
      apiKey: "bb36eeb928454b369f0a84b7b0474504",

      resources: [],
      url: "https://newsapi.org/v2/top-headlines?sources=techcrunch&apiKey=",
      key: "bb36eeb928454b369f0a84b7b0474504",
      message: ""
    };
  },
  methods: {
    getSources: function() {
      let endPoint =
        this.baseUrl +
        "sources?language=" +
        this.language +
        "&apiKey=" +
        this.apiKey;
      //console.log("getSources", endPoint);
      axios
        .get(endPoint)
        .then(response => {
          //this.message = response.data.message;
          //console.log("in getSources,axios", response.data.sources[1], "<--");
          this.sources = response.data.sources.map(obj => ({
            id: obj.id,
            name: obj.name
          }));
          console.log("gS", this.sources);
        })
        .catch(error => {
          console.log(error);
        });
      console.log("s", this.sources);
    }
  },

  computed: {
    endPoint: function() {
      return this.url + this.key;
    }
  },

  components: {},
  props: {},
  created: function() {
    console.log("created");
    this.getSources();
    console.log(this.url + this.key);
    axios
      .get(this.url + this.key)
      .then(response => {
        this.message = response.data.message;
        console.log("t.m", this.message);
        console.log(response);
      })
      .catch(error => {
        console.log(error);
      });
  },
  mounted: function() {
    console.log("mounted:", this.sources);
  }
};
</script>

<style scoped>
</style>
