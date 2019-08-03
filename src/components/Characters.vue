<template lang="html">
  <div>
    <h3>Hello this is characters.vue</h3>

    <ul>

        <li v-for="character in characters">
          <router-link :to="{name: 'character', params: { id: character.id}}">{{character.name}}</router-link>
        </li>
      </ul>
  </div>
</template>

<script>
import { public_key } from "./../secrets.js";
import axios from "axios";

export default {
  name: "Characters",
  data() {
    return {
      characters: []
    };
  },
  methods: {
    getCharacters() {
      const public_key = "a8baca49d74454a48df4c79b894b164d";
      axios
        .get(
          "http://gateway.marvel.com/v1/public/characters?apikey=" + public_key
        )
        .then(result => {
          result.data.data.results.forEach(item => {
            this.characters.push(item);
          });
        })
        .catch(error => {
          console.log(error);
        });
    }
  },
  mounted() {
    this.getCharacters();
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
/*ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}*/
</style>
