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
                            <button v-on:click="saveUser();register();" class="btn btn-large grey lighten-4 black-text" type="submit">Register</button>
                        </form>
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
            email:'',
            password:'',
            name: null,
            owner: false
        }
    },
    methods: {
    register: function(e) {
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
      e.preventDefault();
    },
    saveUser () {
      db.collection('user').add({
        email: this.email,
        name: this.name,
        owner: this.owner
      })
      .then(docRef => {
        console.log('Client added: ', docRef.id)
        this.$router.push('/dashboard')
      })
      .catch(error => {
        console.error('Error adding employee: ', error)
      })
    }
  }
};
</script>
