<template>
  <div id="">
    <v-dialog v-model="showModal">
      <v-card>
        <v-card-text>
          <h2 class="title">Get Me In The Queue</h2>
          <form>
            <label for="name">Name</label>
            <input type="text" name="name" placeholder="Tredegar" v-model='player.name'>
          </form>
        </v-card-text>
          <v-spacer></v-spacer>
          <v-btn flat @click="closeModal" class="primary">Cancel</v-btn>
          <v-btn flat  @click="closeAndPost" class="primary" >Submit</v-btn>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
import AddToQueueButton from '@/components/AddToQueueButton'

export default {
  name: "AddItemModal",
  data() {
    return {
      player:{
        name: ""
      },
      databaseUrl: 'https://whos-got-next-server.herokuapp.com/'
    }
  },
  methods: {
    playerPost(name){
      return fetch(this.databaseUrl, {
        method: "POST",
        body: JSON.stringify(this.player),
        headers: new Headers({
    'Content-Type': 'application/json'})
      })
      .then(resp => resp.json())
    },
    closeAndPost(){
      this.playerPost(this.player)
      .then(() => {
        this.playersGet()
        this.closeModal()
      })
    }
  },
  components: {
    AddToQueueButton
  },
  props: ['showModal', 'closeModal', 'playersGet']
}</script>
<style scoped>
</style>
