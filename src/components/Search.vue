<template>
  <div class="container fluid">
    <div class="search-wrapper">
    <!-- the search bar form -->
      <form v-on:submit="getfilteredData">
        <div class="form-row">
          <div class="col-12">
            <input type="text" class="form-control" placeholder="Enter key word  ..." v-model="search" v-on:keyup="getfilteredData">
          </div>
        </div>
      </form>
  </div>
   <div class="card-columns">
    <!-- iterate firebasedata -->
    <div v-for="(item, index) in firebaseData" :key="index">
    <router-link v-bind:to="{ name: 'apartment-info', params: { ap_id: item.ap_id }}"><apartment-card :item="item"></apartment-card></router-link>
    </div>
   </div>
  </div>
</template>
<script>
import ApartmentCard from './ApartmentCard';
import db from './firebaseInit'
export default {
  name: 'search',
  components: {
    'apartment-card': ApartmentCard
  },
  computed: {
    selectedFilters: function() {
      let filters = [];
      let checkedFiters = this.stacks.filter(obj => obj.checked);
      checkedFiters.forEach(element => {
        filters.push(element.value);
      });
      return filters;
    }
  },
  data() {
    return {
      firebaseData: [],
      firebaseDB: [],
      loading: true,
      search: '',
      stacks: [
      {
        checked: false,
        value: 'language'
      },
      {
        checked: false,
        value: 'framework'
      },
      {
        checked: false,
        value: 'frontend'
        },
      {
        checked: false,
        value: 'backend'
      },
      {
        checked: false,
        value: 'mobile'
      },
      {
        checked: false,
        value: 'web'
      },
      {
        checked: false,
        value: 'hybrid'
      },
      {
        checked: false,
        value: 'database'
      }
      ]
    };
  },
  methods: {
    getfilteredData: function() {
      this.firebaseData = this.firebaseDB
      let filteredFirebaseDataByfilters = [];
      let filteredFirebaseDataBySearch = [];
      if (this.search !== '') {
        filteredFirebaseDataBySearch = this.firebaseData.filter(obj => obj.name.toLowerCase().indexOf(this.search.toLowerCase()) >= 0);
        this.firebaseData = filteredFirebaseDataBySearch;
      }
    },
    setfirebaseData: function() {
        db.collection('test').orderBy('id').get().then((querySnapshot) => {
        this.loading = false
        querySnapshot.forEach((doc) => {
          const data = {
            id: doc.id,
            ap_id: doc.data().ap_id,
            image: doc.data().image,
            name: doc.data().name,
            location: doc.data().location,
            price: doc.data().price,
            tyAp: doc.data().tyAP
          }
          this.firebaseDB.push(data)
        })
      })
    }
  },
  mounted() {
    this.setfirebaseData();
    this.getfilteredData();
  }
};
</script>
