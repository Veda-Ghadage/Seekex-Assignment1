<template>
  <div style="margin: 20px">
      <h2 style="text-align: center">Employee Details</h2>
      <v-row>
        <v-col v-for="pdata in postsdata.data" :key="pdata.id" lg="4" md="6">
          <v-card
          class="mx-auto"
          outlined
          >
           <v-list-item three-line>
      <v-list-item-content>
        <v-list-item-title>
          Name: {{pdata.employee_name}}
        </v-list-item-title>
        <v-list-item-subtitle>
          <ul>
            <li>Employee Salary: {{pdata.employee_salary}}</li>
            <li>Employee Age: {{pdata.employee_age}}</li>
          </ul>
        </v-list-item-subtitle>
      </v-list-item-content>

      <v-list-item-avatar
        tile
        size="80"
        color="grey"
      >
        <img :src="pdata.profile_image" alt="">
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
  created () {
    this.getdata()
  },
  // mounted () {
  //   this.getdata()
  // },
  methods: {
    getdata () {
      axios.get('https://dummy.restapiexample.com/api/v1/employees').then((res) => {
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
