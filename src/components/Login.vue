<template>
    <div class="font-kanit">
        <div class="container">
            <div class="row">
                <div class="col s12">
                    <div class="login card-panel white black-text center">
                        <h3>Login</h3>
                        <form >
                            <div class="input-field">
                                <i class="material-icons prefix">email</i>
                                <input type="text" id="email" v-model="email">
                                <label for="email" class="black-text">Email</label>
                            </div>
                            <div class="input-field">
                                <i class="material-icons prefix">lock</i>
                                <input type="password" id="password" v-model="password">
                                <label for="password" class="black-text">Password</label>
                            </div>
                            <button v-on:click="login" class="btn btn-large grey lighten-4 black-text font-kanit">Login</button>
                        </form>
                        <br>
                        <a href="#/register">Don't have an account? Register here</a>
                        <br>
                        <rounter-link v-on:click="googleSignIn()"><img src="/static/google-authen.png" class="google-authen"></rounter-link>
                        
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import firebase from 'firebase';
export default {
  name: 'login',
  data: function() {
    return {
      email: '',
      password: ''
    };
  },
  methods: {
    login: function(e) {
      firebase.auth().signInWithEmailAndPassword(this.email, this.password).then(user => {
            alert(`You are logged in as ${user.user.email}`);
            this.$router.go({ path: this.$router.path });
          },
          err => {
            alert(err.message);
          }
        );
      e.preventDefault();
    },
    googleSignIn () {
        this.provider = new firebase.auth.GoogleAuthProvider()
        firebase.auth().signInWithPopup(this.provider).then(result => {
          // store the user ore wathever
          this.$router.go({ path: this.$router.path });
        }).catch(e => {
          this.$snotify.error(e.message)
          console.log(e)
        })
      }
  }
};
</script>

<style >
.font-kanit {
  font-family: 'Kanit', sans-serif;
}
.google-authen {
  width: 307px;
  height: 67px;
  left: 200px;

  /* background: url(google-authen.png); */
}
</style>
