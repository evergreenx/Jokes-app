<template>
  <div>
    <v-contanier>
      <joke
        v-for="joke in jokes"
        :key="joke.id"
        :id="joke.id"
        :joke="joke.joke"
      />

      <v-alert outlined dismissible class="" v-show="networkErr">
        {{ networkErr }}
      </v-alert>
    </v-contanier>
  </div>
</template>
<script>
import axios from 'axios';
import joke from '../../components/joke';

export default {
  name: 'index',
  components: {
    joke
  },

  data() {
    return {
      jokes: [],
      networkErr: '',
      snackBar: false
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: 'application/json'
      }
    };

    try {
      const res = await axios.get('https://icanhazdadjoke.com/search', config);

      this.jokes = res.data.results;
    } catch (err) {
      if (err) {
        this.networkErr = 'something is not rigth';
      }
      alert(err);
    }
  },

  head() {
    return {
      title: ' Welcome to joke app ',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Best joke app on the internet'
        }
      ]
    };
  }
};
</script>
