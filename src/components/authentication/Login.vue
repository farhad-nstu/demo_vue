<template>
  <div class="login">
    <div class="loginHeader">
      User Login
    </div>
    <div class="containerHeader">
      <table>
        <tr>
          <td>User Name</td>
          <td>:</td>
          <td><input type="email" placeholder="Email" v-model="email"></td>
        </tr>

        <tr>
          <td>Password</td>
          <td>:</td>
          <td><input type="password" placeholder="Password" v-model="password"></td>
        </tr>

        <tr>
          <td></td>
          <td>:</td>
          <td><button class="addBtn" @click="login">Login</button></td>
        </tr>
      </table>
    </div>
   
  </div>
</template>

<script>
    export default {
      data() {
        return {
          'email': '',
          'password': ''
        }
      },

      methods: {

        login() {
          
          var data = {
            client_id: 2,
            client_secret: 'IROV2pwlGllOb7M84oOg8MJ28UfvSNOjF0848tsQ',
            grant_type: 'password',
            username: this.email,
            password: this.password
          }
          this.$http.post("oauth/token", data)
              .then(response => {
                this.$auth.setToken(response.body.access_token, response.body.expires_in + Date.now())

                this.$router.push("/feed")
              })
              /*.then(function(response) {
                console.log(response);
              });*/
        }
      }
    }
</script>

<style>

</style>