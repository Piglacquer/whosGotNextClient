<template>
  <div id="">
    <ul>
      <ListItem v-for='player in playersInLine.players' :key='player.id' :player='player' :databaseUrl='databaseUrl' :playersGet='playersGet'/>
    </ul>
    <v-container grid-list-md text-xs-center>
      <v-layout row wrap>
        <v-flex xs12>
          <AddItemButton :playerPost='playerPost' :player='player' :captureData='captureData' :playersInLine='playersInLine' :playersGet='playersGet'/>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>
<script>
import ListItem from '@/components/ListItem'
import AddItemButton from '@/components/AddItemButton'

export default {
  name: "NextList",
  data() {
    return {

    }
  },
  components: {
    ListItem,
    AddItemButton
  },
  props: ['playersInLine', 'databaseUrl', 'playersGet', 'playerPost', 'captureData', 'player']
}</script>
<style scoped>
</style>
