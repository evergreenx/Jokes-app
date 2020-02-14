<template>
  <div>
    <nuxt-link to="'jokes/' + id">
      <v-card color="secondary" class="ma-4 pa-2">
        <v-card-title class="headline"></v-card-title>

        <v-card-subtitle>
          {{ joke }}
        </v-card-subtitle>

        <v-card-actions> </v-card-actions>
      </v-card>
    </nuxt-link>
  </div>
</template>

<script>
export default {
  name: 'joke',
  props: ['joke', 'id']
};
</script>

<style scoped>
a {
  text-decoration: none;
}
</style>
