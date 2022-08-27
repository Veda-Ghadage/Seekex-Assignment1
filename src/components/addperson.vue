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
      v-model="salary"
      :rules="salaryRules"
      label="Salary"
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
      Reset Form
    </v-btn>

  </v-form>
    </v-card>
</template>

<script>
import axios from 'axios'

export default {
  data: () => ({
    valid: true,
    successmsg: false,
    name: '',
    nameRules: [
      v => !!v || 'Name is required'
    ],
    salary: '',
    salaryRules: [
      v => !!v || 'Salary is required'
    ],
    age: '',
    ageRules: [
      v => !!v || 'Age is required'
    ],
    country: '',
    countryRules: [
      v => !!v || 'Country is required'
    ],
    avatar: '',
    avatarRules: [
      v => !!v || 'Image is required'
    ]
  }),

  methods: {
    validate () {
      if (this.$refs.form.validate()) {
        console.log(this.name)
        console.log(this.email)
        console.log(this.age)
        console.log(this.country)
        console.log(this.avatar)
        const empdata = {
          name: this.name,
          salary: this.email,
          age: this.age
        }
        // const headers = {
        //   'User-Agent': 'googlebot',
        //   'Access-Control-Allow-Origin': '*',
        //   'Content-Type': 'application/json'
        // }
        axios.post('https://dummy.restapiexample.com/api/v1/create', empdata).then((res) => {
          console.log(res)
          this.successmsg = true
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
