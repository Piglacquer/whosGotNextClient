<template>
  <div>
    <v-btn @click='playerRemove()' flat icon color="red lighten-2">
      <v-icon>block</v-icon>
    </v-btn>
  </div>
</template>
<script>
export default {
  name: "DeleteItemButton",
  data() {
    return {
    }
  },
  methods: {
    },
    props: ['playerRemove', 'playerId', 'playersGet', 'databaseUrl']
  }</script>
<style scoped>
</style>
