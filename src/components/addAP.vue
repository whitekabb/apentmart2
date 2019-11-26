<template>
  <div class="font-kanit">
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
          <input type="text" v-model="owner" required>
          <label>Owner</label>
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
        <router-link to="/apManagement" class="btn grey">Cancel</router-link>
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
      owner: null,
      price: null,
      tyAP: null,
      description: null,
      initialFee: null,
      insuranceFee: null
    }
  },
  methods: {
    saveEmployee () {
      db.collection('Apartment').add({
        ap_id: this.ap_id,
        name: this.name,
        location: this.location,
        owner: this.owner,
        price: this.price,
        tyAP: this.tyAP,
        description: this.description,
        initialFee: this.initialFee,
        insuranceFee: this.insuranceFee
      })
      .then(docRef => {
        console.log('Client added: ', docRef.id)
        this.$router.push('/')
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