<template>
  <div class="card p-3">
    <div class="text-center">
      <img class="img-fluid" v-bind:src="item.image" width="300" alt="Card   image cap">
      <div class="card-body">
        <h5 class="card-title">{{ item.name | capitalize }} </h5>
      </div>
      <div class="right">
        <router-link v-bind:to="{ name: 'apartment-info', params: { id: item.id }}" class="btn-floating btn-large blue">
          <i class="material-icons">add</i>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name:'apartment-card',
    // list of tags to giving each stack a different color
      tags: {
        language: 'light',
        framework: 'dark',
        frontend: 'success',
        backend: 'danger',
        mobile: 'warning',
        web: 'secondary',
        hybrid: 'info',
        database: 'danger'
      },
      image: ''
    };
  },
  filters: {
   // this filter will can be used to capitalize a word
    capitalize: item => {
      return item.toUpperCase();
    }
  },
  props: {
    // this component expects a prop of type object
    item: {
      type: Object,
      required: true
    }
  }

};
</script>
