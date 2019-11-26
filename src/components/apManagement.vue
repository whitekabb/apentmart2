<template>
  <div class="font-kanit">
    <div class="container">
      <div>
        <div class="card light-blue lighten-2 col s12 m4 l8 head-height">
          <h4 class="text-center white-text head-padding" > การจัดการหอพัก </h4>
        </div>

        <div v-if="firebaseData.lenght">
            <h1>1</h1>
        </div>

        <div class="">
          <div v-for="(item,index) in firebaseData" :key="index">
            <div class="card hoverable">
              <div class="card-image">
                <img v-bind:src="item.image" height="250px" alt="Card image cap">
              </div>
                <div class="card-content">
                  <h5 class="card-title">{{ item.name | capitalize }} </h5>
                  <p class="text-left">{{item.description}}</p>
                </div>
            </div>
          </div>
        </div>

        <div class="card light-blue lighten-4 col s12 m4 l8 add-height">
          <div class="btn-padding center">
              <router-link v-bind:to="{ name: 'addAP', params: { email: this.email }}" class="btn-floating btn-large"><i class="material-icons">add</i></router-link>
          </div>
        </div>
          <!-- <router-link to="/" class="btn-floating container"><i class="material-icons">add</i></router-link> -->

      </div>
    </div>
  </div>
</template>

<script>
import firebase from 'firebase'
import db from './firebaseInit'
export default {
  name: 'apManagement',
  data() {
    return {
      email: null,
      name: null,
      tel: null,
      firebaseData: [],
      loading: true
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
            this.tel = doc.data().tel
            finddata()
          })
        })
        
      },finddata: function() {
        db.collection('Apartment').where('email', '==', this.$route.params.email).get().then((querySnapshot) => {
        this.loading = false
        querySnapshot.forEach((doc) => {
          const data = {
            'ap_id': doc.data().ap_id,
            'name': doc.data().name,
            'location': doc.data().location,
            'email': doc.data().email,
            'price': doc.data().price,
            'tyAP': doc.data().tyAP,
            'description': doc.data().description,
            'initialFee': doc.data().initialFee,
            'insuranceFee': doc.data().insuranceFee
          }
          this.firebaseData.push(data)
        })
      })
      }
    }
}
</script>

<style>

.head-padding {
  padding-top: 10px
}

.head-height {
  height: 100px;
}

.add-height {
  height: 300px;
}

.btn-padding {
  padding-top: 115px;
}

</style>
