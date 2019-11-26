<template>
  <div id="view-employee" class="container">
    <ul class="collection with-header">
      <li class="collection-header"><h4>{{email}}</h4></li>
      <li class="collection-item">Name: {{name}}</li>
      <li class="collection-item">Owner status: {{owner}}</li>
      <li class="collection-item">Phone number: {{tel}}</li>
      <!-- <li class="collection-item">Position: {{email}}</li>  -->
    </ul>

    <div class="right">
      <router-link v-bind:to="{ name: 'edit-profile', params: { email: email }}" class="btn-floating btn-large blue">
        <i class="material-icons">edit</i>
      </router-link>
    </div>
  </div>
</template>

<script>
  import db from './firebaseInit'
  export default {
    name: 'profile',
    data () {
      return {
        email: null,
        name: null,
        tel: null,
        owner: null
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
    }
  }
</script>