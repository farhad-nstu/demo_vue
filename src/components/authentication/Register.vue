<template>
  <div class="login">
    <div class="loginHeader">
      User Register
    </div>
    <div class="containerHeader">
      <table>

        <tr>
          <td>User Name</td>
          <td>:</td>
          <td><input type="text" placeholder="Name" v-model="name"></td>
        </tr>
        <tr>
          <td>User Email</td>
          <td>:</td>
          <td><input type="email" placeholder="Email" v-model="email"></td>
        </tr>

        <tr>
          <td>Password</td>
          <td>:</td>
          <td><input type="password" placeholder="password" name="password" v-model="password"></td>
        </tr>

        <tr>
          <td></td>
          <td>:</td>
          <td><button class="addBtn">Register</button></td>
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
          'password': '',
          'name': ''
        }
      }
    }
</script>

<style>

</style>