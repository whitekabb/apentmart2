<template>
  <div id="apartment-info" class="container" >
    <br>
      <div class="row text-center">
        <div class="col s12 header light-blue lighten-4"><span><h4>{{name}}</h4></span></div>
      </div>
      <div class="row">
        <div class="col s4">
          <img v-bind:src="image" height="400px" width="550px" >
        </div>
        <div class="col s6">
          <span><h4>{{name}}</h4></span>
          <span><h1> </h1></span>
          <span><h5 class="light-blue-text">รายละเอียดหอพัก</h5></span>
          <span><p>{{description}}</p></span>
          <span><h1> </h1></span>
          <span><h5 class="light-blue-text">รายละเอียดค่าแรกเข้า</h5></span>
          <span><p>ค่ามัดจำล่วงหน้า : {{insuranceFee}} บาท</p></span>
          <span><p>ค่าเช่ารายเดือน   : {{price}} บาท</p></span>
          <span><p>______________________________</p></span>
          <span><p>สรุปรวมค่าแรกเข้า: {{initialFee}} บาท</p></span>
        </div>
        <div class="row">
        <div class="col s10 text-center">
          <span><h1 class="light-blue-text">____________________________________</h1></span>
        </div>
      </div>
      </div>
      <div class="row">
        <div class="col s10 text-center">
          <img v-bind:src="'/static/home/map.png'">
        </div>
      </div>
      <div class="row">
        <div class="col s10">
          <button type="submit" v-on:click="getback" class="btn grey right">Back</button>
        </div>
      </div>
    
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
        tyAp: null,
        description: null,
        initialFee: null,
        insuranceFee: null,
        facebook: null
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
            vm.description=doc.data().description
            vm.initialFee=doc.data().initialFee
            vm.insuranceFee = doc.data().insuranceFee
            vm.facebook = doc.data().facebook
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
            this.tyAp= doc.data().tyAP,
            this.description=doc.data().description
            this.initialFee=doc.data().initialFee
            this.insuranceFee = doc.data().insuranceFee
            this.facebook = doc.data().facebook
          })
        })
      },
      getback: function () {
        this.$router.go(-1)
      }
    }
  }

</script>