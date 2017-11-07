<template>
  <b-container>
    <b-row>
      <b-col class="text-left" md="4" offset-md="4">
        <h1>Register New User</h1>
        <b-form>
          <b-form-group
            label="Email:">
            <b-form-input
              type="email" 
              v-model="email" 
              required
              placeholder="Enter email"
            ></b-form-input>
          </b-form-group>
          <b-form-group
            label="Password:">
            <b-form-input
              type="password" 
              v-model="password" 
              required
              placeholder="Enter password"
            ></b-form-input>
          </b-form-group>
          <b-alert variant="danger"dismissible
                  :show="error"
                  @dismissed="error=null">
            <div v-html="error"></div>
          </b-alert>
          
          <b-button type="submit" @click="register" variant="primary">Submit</b-button>
        </b-form>
      </b-col>
    </b-row>
  </b-container>
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
</style>
