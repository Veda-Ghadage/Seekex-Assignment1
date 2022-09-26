<template>
  <div style="margin: 20px">
      <h2 style="text-align: center">Details</h2>
      <v-row>
        <v-col v-for="pdata in postsdata" :key="pdata.id" cols="12" lg="4" sm="s">
          <v-card
          class="mx-auto"
          outlined
          >
           <v-list-item three-line>
      <v-list-item-content>
        <v-list-item-title>
          Name: {{pdata.name}}
        </v-list-item-title>
        <v-list-item-subtitle>
          <ul>
            <li>Age: {{pdata.age}}</li>
            <li>Colour: {{pdata.colour}}</li>
          </ul>
        </v-list-item-subtitle>
      </v-list-item-content>

      <v-list-item-avatar
        tile
        size="80"
        color="grey"
      >
        <img src="https://png.pngtree.com/png-vector/20191021/ourlarge/pngtree-user-vector-icon-with-transparent-background-png-image_1836030.jpg" alt="">
      </v-list-item-avatar>
    </v-list-item>
          </v-card>
        </v-col>
      </v-row>
  </div>
</template>
<script>
import axios from 'axios'
// import.meta.env.VUE_API_CODE

export default {
  data: () => ({
    API_CODE: '97dafb82fa2649799bd6aa668b4e94f6',
    postsdata: []
  }),
  created () {
    this.getdata()
  },
  methods: {
    getdata () {
      axios.get(`https://crudcrud.com/api/${this.API_CODE}/test`).then((res) => {
        console.log(res.data)
        this.postsdata = res.data
        console.log(this.postsdata)
      }).catch((err) => {
        console.log(err)
      })
    }
  }
}
</script>
