<template>
  <div id="">
   <v-card light>
     <v-container grid-list-sm text-sm-center text-md-center>
       <v-layout row nowrap>
           <v-card-title primary-title>
             <div>
               <h3 class="headline mb-0">{{player.name}}</h3>
             </div>
           </v-card-title>
          <v-flex class="txt-lg-right">
            <v-card-actions>
             <DeleteItemButton :playerRemove='playerRemove' :playerId='player.id' :playersGet='playersGet'  :databaseUrl='databaseUrl'/>
           </v-card-actions>
         </v-flex>
       </v-layout>
     </v-container>
   </v-card>
  </div>
</template>
<script>
import DeleteItemButton from '@/components/DeleteItemButton'

export default {
  name: "ListItem",
  data() {
    return {}
  },
  props: ['player', 'databaseUrl', 'playersGet'],
  components: {
    DeleteItemButton
  },
  methods: {
    playerRemove(){
      console.log('listentoMe')
      fetch(this.databaseUrl + this.player.id, {
        method: 'DELETE'
      }).then(()=> {
        console.log('im running')
        this.playersGet()
      })
    }
  },
  mounted(){
  }
}</script>
<style scoped>
li {
  font-size: 3rem;
}
</style>
