<template>
 <v-card
    class="mx-auto"
    max-width="600"
    style="margin-top: 50px; padding: 20px"
    outlined
  >
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
      v-model="email"
      :rules="emailRules"
      label="E-mail"
      required
    ></v-text-field>

    <v-text-field
      v-model="age"
      :rules="ageRules"
      label="Age"
      required
    ></v-text-field>

    <v-text-field
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
    ></v-text-field>

    <v-btn
      :disabled="!valid"
      color="success"
      class="mr-4"
      @click="validate"
    >
      Validate
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
    name: '',
    nameRules: [
      v => !!v || 'Name is required'
    ],
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required'
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
        const article = {
          name: this.name,
          email: this.email,
          dob: this.age,
          country: this.country,
          avatar: this.avatar
        }
        const headers = {
          'User-Agent': 'googlebot',
          'Content-Type': 'application/json'
        }
        axios.post('https://tekdi-challenges.appspot.com/api/People', article, { headers }).then((res) => {
          console.log(res)
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
