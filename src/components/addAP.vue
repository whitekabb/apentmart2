<template>
  <div class="font-kanit container">
    <h3>Add AP</h3>
    <div class="row">
    <form @submit.prevent="saveEmployee" class="col s12">
      <div class="row">
        <div class="input-field col s12">
          <input type="text" v-model="ap_id" required>
          <label>AP_ID#</label>
        </div>
      </div>
      <div class="row">
        <div class="input-field col s12">
          <input type="text" v-model="name" required>
          <label>Name</label>
        </div>
      </div>
      <div class="row">
        <div class="input-field col s12">
          <input type="text" v-model="location" required>
          <label>Location</label>
        </div>
      </div>
      <div class="row">
        <div class="input-field col s12">
          <input type="text" v-model="tyAP" required>
          <label>Type - Aparment</label>
        </div>
      </div>
      <div class="row">
        <div class="input-field col s12">
          <input type="text" v-model="price" required>
          <label>Price</label>
        </div>
      </div>
      <div class="row">
        <div class="input-field col s12">
          <input type="text" v-model="email" required>
          <label>Owner email</label>
        </div>
      </div>
      <div class="row">
        <div class="input-field col s12">
          <input type="text" v-model="description" required>
          <label>Description</label>
        </div>
      </div>
      <div class="row">
        <div class="input-field col s12">
            <input type="text" v-model="initialFee" required>
          <label>InitialFee</label>
        </div>
      </div>
      <div class="row">
        <div class="input-field col s12">
          <input type="text" v-model="insuranceFee" required>
          <label>InsuranceFee</label>
        </div>
      </div>
      <button type="submit" class="btn">Submit</button>
        <router-link v-bind:to="{ name: 'apManagement', params: { email: this.email }}" class="btn grey">Cancel</router-link>
    </form>
  </div>
  </div>
</template>

<script>
import db from './firebaseInit'
export default {
  data () {
    return {
      ap_id: null,
      name: null,
      location: null,
      price: null,
      tyAP: null,
      description: null,
      initialFee: null,
      insuranceFee: null,
      email:null
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
          })
        })
        },
    saveEmployee () {
      db.collection('Apartment').add({
        ap_id: this.ap_id,
        name: this.name,
        location: this.location,
        email: this.email,
        price: this.price,
        tyAP: this.tyAP,
        description: this.description,
        initialFee: this.initialFee,
        insuranceFee: this.insuranceFee
      })
      .then(docRef => {
        console.log('Client added: ', docRef.id)
        this.$router.push({ name: 'apManagement', params: { email: this.email }})
      })
      .catch(error => {
        console.error('Error adding employee: ', error)
      })
    }
  }
}
</script>


<style >
.font-kanit {
  font-family: 'Kanit', sans-serif;
}
</style>