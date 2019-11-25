<template>
    <div>
        <div class="container">
            <div class="row">
                <div class="col s12 m8 offset-m2">
                    <div class="login card-panel white black-text center">
                        <h3>Register</h3>
                        <form>
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
                            <div class="input-field">
                                <i class="material-icons prefix">lock</i>
                                <input type="password" id="cpassword" v-model="cpassword">
                                <label for="password" class="black-text">Confirm password</label>
                            </div>
                            <div class="input-field">
                                <i class="material-icons prefix">assignment_ind</i>
                                <input type="text" id="name" v-model="name">
                                <label for="name" class="black-text">Name</label>
                            </div>
                            <div class="input-field">
                                <!-- <i class="material-icons prefix">lock</i> -->
                                <p>
                                  <label>
                                    <input type="checkbox" class="filled-in" value="true" v-model="owner" />
                                    <span>Owner : {{owner}}</span>
                                  </label>
                                </p>
                                <!-- <input type="password" id="owner" v-model="owner">
                                <label for="password" class="black-text">Owner ()</label> -->
                            </div>
                            <button v-on:click="register" class="btn btn-large grey lighten-4 black-text" type="submit">Register</button>
                        </form>
                        <p v-if="errors.length">
                          <b>Please correct the following error(s):</b>
                          <ul>
                            <li v-for="(error,index) in errors" v-bind:key="index">{{ error }}</li>
                          </ul>
                          <b>Try again.</b>
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import db from './firebaseInit'
import firebase from 'firebase'
export default {
    // name: 'register',

    data: function() {
        return {
            email:null,
            password:null,
            cpassword: null,
            name: null,
            owner: false,
            errors: []
        }
    },
    methods: {
    register: function(e) {
      if (this.email && this.password && this.cpassword && this.password == this.cpassword && this.name ) {
        
        firebase
          .auth()
          .createUserWithEmailAndPassword(this.email, this.password)
          .then(
            user => {
              // console.log(user);
              alert(`Account Created for ${user.user.email}`);
              this.$router.go({ path: this.$router.path });
            },
            err => {
              alert(err.message);
            }
          );
        db.collection('user').add({
          email: this.email,
          name: this.name,
          owner: this.owner
        })
        .catch(error => {
          console.error('Error adding employee: ', error)
        })
        e.preventDefault();

      } else {
        this.errors = [];

        if (!this.email) {
          this.errors.push('email required.');
        }
        if (!this.name) {
          this.errors.push('name required.');
        }
        if (!this.password) {
          this.errors.push('password required.');
        }
        if (!this.cpassword) {
          this.errors.push('Confirm password required.');
        }
        if (!(this.password == this.cpassword)) {
          this.errors.push("Those password didn't match");
        }
        e.preventDefault();
      }
    }
  }
}

</script>
