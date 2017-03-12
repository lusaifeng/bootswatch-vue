<template>
  <div>
    <form class="form-horizontal" @submit.prevent="submit">
        <div class="form-group" v-for="(item,index) in data.fields">
          <label :for="index" :class="'col-lg-' + data.labelSize + ' control-label'">{{item.label}}</label>
          <div :class="'col-lg-' + (12-data.labelSize)">
            <input v-if="item.type == 'text'" type="text" class="form-control" :id="index" :placeholder="item.placeholder" v-model="item.value">
            <input v-if="item.type == 'password'" type="password" class="form-control" :id="index" :placeholder="item.placeholder" v-model="item.value">

          </div>
        </div>
        
        <div class="form-group">
          <div :class="'col-lg-' + (12-data.labelSize) + ' col-lg-offset-' + data.labelSize">
            <button type="reset" class="btn btn-default">重置</button>
            <button type="submit" class="btn btn-primary">提交</button>
          </div>
        </div>
    </form>
  </div>
</template>

<script>
  export default {

    name: 'adForm',
    props: [
      'data'
    ],
    data () {
      return {

      }
    },
    methods: {
      submit: function() {
        var fields = this.data.fields
        var data = {}
        for(var index in fields) {
          data[index] = fields[index].value
          //index = 'username'
          //fields['username'] = {...}
          //data.username = fields['username'].value
          //data[index] = fields[index].value
        }
        
        this.$http.post(this.data.action, data).then((response) => {
          // success callback
        }, (response) => {
          // error callback
        })
      }
    }
  };
</script>

<style lang="scss" scoped>

</style>