<template>
  <div class="card hoverable font-kanit">
    <div class="card-image">
      <img v-bind:src="item.image" height="250px" alt="Card image cap">
    </div>
      <div class="card-content">
        <h5 class="card-title">{{ item.name | capitalize }} </h5>
        <p class="text-left">{{item.description}}</p>
      </div>
  </div>
  
</template>

<script>
export default {
  data() {
    return {
      name:'apartment-card',
    // list of tags to giving each stack a different color
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

<style >
.font-kanit {
  font-family: 'Kanit', sans-serif;
}
</style>
