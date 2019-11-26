<template>
    <nav>
        <div class="nav-wrapper blue font-kanit">
            <div class="container">
                <a href="#/">
                 <img :width="40" v-bind:src="'/static/favicon.png'">
                </a>
                <ul class="right">
                    <li v-if="isLoggedIn"><span class="email bold white-text">Hello {{name}}</span></li>
                    <li v-if="isLoggedIn&&owner"><router-link v-bind:to="{ name: 'apManagement', params: { email: currentUser }}">Manage Apartment</router-link></li>
                    <li><a href="#/search"><i class="material-icons left">search</i>Search</a></li>
                    <li ><router-link to="/">Home</router-link></li>
                    <li v-if="!isLoggedIn"><router-link to="/login">Login</router-link></li>
                    <li v-if="!isLoggedIn"><router-link to="/register">Register</router-link></li>
                    <li v-if="isLoggedIn"><router-link v-bind:to="{ name: 'profile', params: { email: currentUser }}">Profile</router-link></li>
                    <li v-if="isLoggedIn"><button v-on:click="logout" class="btn grey">Log out</button></li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<script>
import firebase from 'firebase';
import db from './firebaseInit'
export default {
  name: 'navbar',
  data() {
    return {
      isLoggedIn: false,
      currentUser: false,
      email: null,
      name: null,
      owner: false
    };
  },
  created() {
    if (firebase.auth().currentUser) {
      this.isLoggedIn = true;
      this.currentUser = firebase.auth().currentUser.email;
      db.collection('user').where('email', '==', this.currentUser).get().then((querySnapshot) => {
          querySnapshot.forEach((doc) => {
            this.email = doc.data().email
            this.name = doc.data().name
            this.owner = doc.data().owner
          })
        })
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
.font-kanit {
  font-family: 'Kanit', sans-serif;
}
</style>