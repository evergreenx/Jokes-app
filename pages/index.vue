<template>
  <div>
    <v-contanier>
      <p>
        Welcome to joke - app .org ,The Best joke app on the internet
      </p>
    </v-contanier>
    {{ jokes }}
    <v-btn @click="on"> click me </v-btn>
  </div>
</template>
<script>
import axios from 'axios';
export default {
  data() {
    return {
      jokes: []
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
      alert(res);
    } catch (err) {
      alert(err);
    }
  },
  methods: {
    on() {
      window.console.log(this.jokes);
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
