<template>
  <div id="apartment-info">
    <ul class="collection with-header">
      <li class="collection-header"><h4>{{name}}</h4></li>
      <!-- <li class="collection-item">Employee ID#: {{employee_id}}</li>
      <li class="collection-item">Department: {{dept}}</li>
      <li class="collection-item">Position: {{position}}</li> -->
    </ul>
    <router-link to="/search" class="btn grey right">Back</router-link>
    <!-- <button @click="deleteEmployee" class="btn red">Delete</button> -->
<!-- 
    <div class="fixed-action-btn">
      <router-link v-bind:to="{ name: 'edit-employee', params: { employee_id: employee_id }}" class="btn-floating btn-large blue">
        <i class="material-icons">edit</i>
      </router-link>
    </div> -->
  </div>
</template>

<script>
  import db from './firebaseInit'
  export default {
    name: 'apartment-info',
    data () {
      return {
        id: null,
        ap_id: null,
        image: null,
        name: null,
        location: null,
        price: null,
        tyAp: null
        }
    },
    beforeRouteEnter (to, from, next) {
      db.collection('Apartment').where('ap_id', '==', to.params.ap_id).get().then((querySnapshot) => {
        querySnapshot.forEach((doc) => {
          console.log(doc)
          next(vm => {
            vm.id= doc.data().id
            vm.ap_id= doc.data().ap_id
            vm.image= doc.data().image
            vm.name= doc.data().name
            vm.location= doc.data().location
            vm.price= doc.data().price
            vm.tyAp= doc.data().tyAP
          })
        })
      })
    },
    watch: {
      '$route': 'fetchData'
    },
    methods: {
      fetchData () {
        db.collection('Apartment').where('ap_id', '==', this.$route.params.ap_id).get().then((querySnapshot) => {
          querySnapshot.forEach((doc) => {
            this.id= doc.data().id,
            this.ap_id= doc.data().ap_id,
            this.image= doc.data().image,
            this.name= doc.data().name,
            this.location= doc.data().location,
            this.price= doc.data().price,
            this.tyAp= doc.data().tyAP
          })
        })
      }
    }
  }

</script>