<template>
  
    <div class="header clearfix">
    	<h3 class="text-muted">Project name</h3>
        <nav class="pull-right" style="margin-left: 400px;">
          
          <ul class="nav nav-pills pull-right">
            
            <router-link tag="li" to='/login' v-if=" ! isAuth">
              <a href="">Login</a>
            </router-link>
         
            <router-link tag="li" to='/register' v-if=" ! isAuth">
              <a href="">Register</a>
            </router-link>

            <router-link tag="li" to='/feed' v-if="isAuth">
              <a href="">Feed</a>
            </router-link>
         
            <router-link tag="li" to='/logout' v-if="isAuth">
              <a href="">Logout</a>
            </router-link>
          
            <!-- <li role="presentation" class="active"><a href="#" style="margin-right: 10px;">Home</a></li>
            <li role="presentation"><a href="#" style="margin-right: 10px;">About</a></li>
            <li role="presentation"><a href="#">Contact</a></li> -->
          </ul>
        </nav>
        
      </div>
  
</template>

<script>

export default {
  data () {
    return {
      isAuth: null
    }
  },

  created () {
    this.isAuth = this.$auth.isAuthenticated()
    this.setAuthenticatedUser()
  },

  methods: {
    setAuthenticatedUser () {
      this.$http.get('api/user')
          .then(response => {
            this.$auth.setAuthenticatedUser(response.body)

            console.log(this.$auth.getAuthenticatedUser())
          })
    }
  }
}
</script>

<style>
 .router-link-active {
  background-color: green;
  color: red;
 }
</style>
