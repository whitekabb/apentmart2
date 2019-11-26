<template>
  <div id="new-employee" class="container">
    <h3>Edit Employee</h3>
    <div class="row">
    <form @submit.prevent="updateEmployee" class="col s12">
      <div class="row">
          
        <div class="input-field col s12">
            <p>Name :</p>
          <input type="text" v-model="name" required>
        </div>
      </div>
      <div class="row">
        <div class="input-field col s12">
            <p>Phone number :</p>
          <input type="text" v-model="tel">
        </div>
      </div>
      <button type="submit" class="btn">Submit</button>
      <router-link to="/dashboard" class="btn grey">Cancel</router-link>
    </form>
  </div>
  </div>
</template>

<script>
  import db from './firebaseInit'
  export default {
    name: 'edit-employee',
    data () {
      return {
        email: null,
        name: null,
        tel: null
      }
    },
    beforeRouteEnter (to, from, next) {
      db.collection('user').where('email', '==', to.params.email).get().then((querySnapshot) => {
        querySnapshot.forEach((doc) => {
          next(vm => {
            vm.email = doc.data().email
            vm.name = doc.data().name
            vm.owner = doc.data().owner
            vm.tel = doc.data().tel
          })
        })
      })
    },
    watch: {
      '$route': 'fetchData'
    },
    methods: {
      fetchData () {
        db.collection('user').where('email', '==', this.$route.params.email).get().then((querySnapshot) => {
          querySnapshot.forEach((doc) => {
            this.email = doc.data().email
            this.name = doc.data().name
            this.owner = doc.data().owner
            this.tel = doc.data().tel
          })
        })
      },
      updateEmployee () {
        db.collection('user').where('email', '==', this.$route.params.email).get().then((querySnapshot) => {
          querySnapshot.forEach((doc) => {
            doc.ref.update({
              name: this.name,
              tel: this.tel
            })
            .then(() => {
              this.$router.push({ name: 'profile', params: { email: this.email }})
            });
          })
        })
      }
    }
  }
</script>