<template>
  <v-layout row>
    <v-flex xs12 sm4 offset-sm4>
      <v-card>
        <v-card-title primary-title>
          <div>
            <div class="headline">Register</div>
          </div>
        </v-card-title>
        <v-card-text>
          <v-text-field
            label="Email"
            v-model="email"
            required
          ></v-text-field>
          <v-text-field
            label="Password"
            v-model="password"
            type="password"
            required
          ></v-text-field>
          <div v-html="error" class="error"></div>
        </v-card-text>
        <v-card-actions>
          <v-btn flat color="orange" @click="register">SUBMIT</v-btn>
        </v-card-actions>
        
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
export default {
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async register () {
      try {
        await AuthenticationService.register({
          email: this.email,
          password: this.password
        })
        this.error = null
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error {
  color: red;
  background-color: white !important;
  text-align: left;
}
</style>
