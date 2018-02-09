<template>
  <v-container fluid='fluid' class='text-xs-center'>
    <AddItemModal v-if="showModal" :showModal='showModal' :closeModal='closeModal' :playersGet='playersGet'/>
    <v-flex xs12 sm6>
          <div>
            <v-btn color="primary" id="show-modal" @click="showModal = true" large>I'm in...</v-btn>
          </div>
    </v-flex>
  </v-container>
</template>

<script>
import AddItemModal from '@/components/AddItemModal'

export default {
  name: "AddItemButton",
  data() {
    return {
      showModal: false
    }
  },
  components: {
    AddItemModal
  },
  methods: {
    closeModal(){
      this.showModal = false
    }
  },
  props:['playersGet']
}</script>
<style scoped>
</style>
