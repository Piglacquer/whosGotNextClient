<template>
  <v-app dark>
    <v-layout>
      <v-flex>
        <v-card text-md-center text-sm-center>
          <v-card-title>
            <h1>Who's Next?</h1>
          </v-card-title>
        </v-card>
        <NextList :playersInLine='playersInLine' :databaseUrl='databaseUrl' :playersGet='playersGet' />
      </v-flex>
    </v-layout>
  </v-app>
</template>

<script>
import NextList from '@/components/NextList'
import AddItemButton from '@/components/AddItemButton'

export default {
  data () {
    return {
      databaseUrl: 'https://whos-got-next-server.herokuapp.com/',
      playersInLine: []
    }
  },
  name: 'App',
  components: {
    NextList,
    AddItemButton
  },
  methods: {
    playersGet(){
      fetch(this.databaseUrl)
      .then(resp => resp.json())
      .then(resp => this.playersInLine = resp)
    }
  },
  mounted(){
    this.playersGet()
  }
}</script>
