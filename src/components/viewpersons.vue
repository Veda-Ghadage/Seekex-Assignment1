<template>
  <div>
      <v-row>
        <v-col v-for="pdata in postsdata" :key="pdata.id" lg="4">
          <v-card
          class="mx-auto"
          max-width="444"
          outlined
          >
           <v-list-item three-line>
      <v-list-item-content>
        <v-list-item-title>
          {{pdata.title}}
        </v-list-item-title>
        <v-list-item-subtitle>{{pdata.body}}</v-list-item-subtitle>
      </v-list-item-content>

      <v-list-item-avatar
        tile
        size="80"
        color="grey"
      >
        <img src="https://t4.ftcdn.net/jpg/02/29/75/83/360_F_229758328_7x8jwCwjtBMmC6rgFzLFhZoEpLobB6L8.jpg" alt="">
      </v-list-item-avatar>
    </v-list-item>
          </v-card>
        </v-col>
      </v-row>
  </div>
</template>
<script>
import axios from 'axios'

export default {
  data: () => ({
    postsdata: []
  }),
  mounted () {
    this.getdata()
  },
  methods: {
    getdata () {
      axios.get('https://jsonplaceholder.typicode.com/posts').then((res) => {
        console.log(res.data)
        this.postsdata = res.data
      }).catch((err) => {
        console.log(err)
      })
    }
  }
}
</script>
