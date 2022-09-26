<template>
 <v-card
    class="mx-auto"
    max-width="600"
    style="margin-top: 50px; padding: 20px"
    outlined
  >
  <v-alert
      dense
      type="success"
      v-if="successmsg"
    >
      Details added successfully
    </v-alert>
  <v-form
    ref="form"
    v-model="valid"
    lazy-validation
  >
    <v-text-field
      v-model="name"
      :rules="nameRules"
      label="Name"
      required
    ></v-text-field>

    <v-text-field
      v-model="colour"
      :rules="colourRules"
      label="Colour"
      required
    ></v-text-field>

    <v-text-field
      v-model="age"
      :rules="ageRules"
      type="number"
      label="Age"
      required
    ></v-text-field>

    <!-- <v-text-field
      v-model="country"
      :rules="countryRules"
      label="Country"
      required
    ></v-text-field>

    <v-text-field
      v-model="avatar"
      :rules="avatarRules"
      label="Image"
      required
    ></v-text-field> -->

    <v-btn
      :disabled="!valid"
      color="success"
      class="mr-4"
      @click="validate"
    >
      Submit
    </v-btn>

    <v-btn
      color="error"
      class="mr-4"
      @click="reset"
    >
      Reset
    </v-btn>

  </v-form>
    </v-card>
</template>

<script>
import axios from 'axios'

export default {
  data: () => ({
    API_CODE: '97dafb82fa2649799bd6aa668b4e94f6',
    valid: true,
    successmsg: false,
    name: '',
    nameRules: [
      v => !!v || 'Name is required'
    ],
    colour: '',
    colourRules: [
      v => !!v || 'Colour is required'
    ],
    age: '',
    ageRules: [
      v => !!v || 'Age is required'
    ]
  }),

  methods: {
    validate () {
      if (this.$refs.form.validate()) {
        console.log(this.name)
        console.log(this.colour)
        console.log(this.age)
        const empdata = {
          name: this.name,
          colour: this.colour,
          age: this.age
        }
        // const headers = {
        //   'User-Agent': 'googlebot',
        //   'Access-Control-Allow-Origin': '*',
        //   'Content-Type': 'application/json'
        // }
        axios.post(`https://crudcrud.com/api/${this.API_CODE}/test`, empdata).then((res) => {
          console.log(res)
          this.successmsg = true
          this.name = ''
          this.colour = ''
          this.age = ''
        }).catch((err) => {
          console.log(err)
        })
      }
    },
    reset () {
      this.$refs.form.reset()
    },
    resetValidation () {
      this.$refs.form.resetValidation()
    }
  }
}
</script>
