<template>
  <div class="font-kanit">
    <div class="container">
      <div>
        <div class="card light-blue lighten-2 col s12 m4 l8 head-height">
          <h4 class="text-center white-text head-padding" > การจัดการหอพัก </h4>
        </div>



        <div class="card light-blue lighten-4 col s12 m4 l8 add-height">
          <div class="btn-padding center">
              <router-link to="/" class="btn-floating btn-large"><i class="material-icons">add</i></router-link>
          </div>
        </div>
          <!-- <router-link to="/" class="btn-floating container"><i class="material-icons">add</i></router-link> -->

      </div>
    </div>
  </div>
</template>



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
