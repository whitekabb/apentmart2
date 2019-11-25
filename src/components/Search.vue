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
      <!-- check boxes -->

  </div>
  <!-- end of checkboxes
  <div class="card-columns">
    iterate data from ./data/data.js
    <item-card v-for="(item, index) in filteredData" :key="index" :item="item"></item-card>
   </div> -->
   <div class="card-columns">
    <!-- iterate firebasedata -->
    <item-card v-for="(item, index) in firebaseData" :key="index" :item="item"></item-card>
   </div>
  </div>
</template>
<script>
import ItemCard from './ItemCard';
import data from '../data/data';
import db from './firebaseInit'
export default {
  name: 'search',
  components: {
    'item-card': ItemCard
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
      loading: true,
      filteredData: [],
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
      this.filteredData = data;
      let filteredDataByfilters = [];
      let filteredDataBySearch = [];
      // first check if filters where selected
    //   if (this.selectedFilters.length > 0) {
    //     filteredDataByfilters= this.filteredData.filter(obj => this.selectedFilters.every(val => obj.stack.indexOf(val) >= 0));
    //     this.filteredData = filteredDataByfilters;
    //   }
      // then filter according to keyword, for now this only affects the name attribute of each data
      if (this.search !== '') {
        filteredDataBySearch = this.filteredData.filter(obj => obj.name.indexOf(this.search.toLowerCase()) >= 0);
        this.filteredData = filteredDataBySearch;
      }
    },
    getfilteredData2: function() {
        db.collection('Apartment').orderBy('id').get().then((querySnapshot) => {
        this.loading = false
        querySnapshot.forEach((doc) => {
          const data = {
            'id': doc.id,
            'image': doc.data().image,
            'name': doc.data().name,
            'location': doc.data().location,
            'price': doc.data().price,
            'tyAP': doc.data().tyAP
          }
          this.firebaseData.push(data)
        })
      })
      let filteredFirebaseDataByfilters = [];
      let filteredFirebaseDataBySearch = [];
      // first check if filters where selected
      if (this.selectedFilters.length > 0) {
        filteredFirebaseDataByfilters= this.firebaseData.filter(obj => this.selectedFilters.every(val => obj.stack.indexOf(val) >= 0));
        this.filteredData = filteredDataByfilters;
      }
      // then filter according to keyword, for now this only affects the name attribute of each data
      if (this.search !== '') {
        filteredFirebaseDataBySearch = this.firebaseData.filter(obj => obj.name.indexOf(this.search.toLowerCase()) >= 0);
        this.firebaseData = filteredDataBySearch;
      }
    }
  },
  mounted() {
    this.getfilteredData();
    this.getfilteredData2();
  }
};
</script>
