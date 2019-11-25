<template>
    <nav>
        <div class="nav-wrapper blue">
            <div class="container">
                <a href="#/">
                 <img :width="40" v-bind:src="'/static/favicon.png'">
                </a>
                <ul class="right">
                    <li v-if="isLoggedIn"><span class="email bold white-text">{{currentUser}}</span></li>
                    <li><a href="#/search"><i class="material-icons left">search</i>Search</a></li>
                    <li ><router-link to="/">Home</router-link></li>
                    <li v-if="!isLoggedIn"><router-link to="/login">Login</router-link></li>
                    <li v-if="!isLoggedIn"><router-link to="/register">Register</router-link></li>
                    <li v-if="isLoggedIn"><button v-on:click="logout" class="btn grey">Log out</button></li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<script>
import firebase from 'firebase';
export default {
  name: 'navbar',
  data() {
    return {
      isLoggedIn: false,
      currentUser: false
    };
  },
  created() {
    if (firebase.auth().currentUser) {
      this.isLoggedIn = true;
      this.currentUser = firebase.auth().currentUser.email;
    }
  },
  methods: {
    logout: function() {
      firebase
        .auth()
        .signOut()
        .then(() => {
          this.$router.go({ path: this.$router.path });
        });
    }
  }
};
</script>

<style scoped>
.email {
  padding-right: 10px;
}
</style>