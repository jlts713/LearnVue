<template>
  <div id="app">
    <h3>Got Jokes?</h3>
    <button class="btn btn-primary" @click="initJokes">Add Ten Random Jokes</button>
    <button class="btn btn-primary" @click="addJoke">Add a Joke</button>
    <br>
    <span v-for="type in types" :key="type">
      <input type="checkbox" :value="type" v-model="checkedTypes" checked>
      <label>{{type}}</label>&nbsp;
    </span>
    <br>
    <div class="coSl-md-12">
      <Joke
        v-for="(joke, idx) in $store.state.jokes"
        v-show="checkedTypes.includes(joke.type)"
        :joke = "joke"
        :key="idx"
        :index="idx"
      >
      </Joke>
    </div>
  </div>
</template>
<script>
import { mapActions } from 'vuex';
import Joke from './Joke.vue';
export default {
  components: {
    Joke,
  },
  data() {
    return {
      types: ['general', 'knock-knock', 'programming'],
      checkedTypes: ['general', 'knock-knock', 'programming'],
    };
  },
  methods: mapActions([
    'initJokes',
    'addJoke',
  ]),  
}
</script>
