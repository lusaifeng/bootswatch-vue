<template>
  <div>
    <ul class="nav nav-tabs">
      <li class="nav-item" 
      @click="active = index" 
      :class="active == index?'active':''" 
      v-for="(item,index) in data">
      <a href="#" class="nav-link">{{index}}</a>
    </li>
  </ul>
  <div class="tab-content">
    <div v-for="(item,index) in data" 
    v-show="active == index"
    role="tabpanel">
    {{item}}
  </div>
</div>
</div>
</template>

<script>
  export default {

    name: 'adTab',
    props: ['data'],
    data () {
      return {
       active: null
     }
    },
    methods: {

    },
    created: function () {
      for(var k in this.data) {
        this.active = k
        break;
      }
    }
  };
</script>

<style lang="scss" scoped>
  .nav {
    margin-bottom: 15px;
  }

</style>