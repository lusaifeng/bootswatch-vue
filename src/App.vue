<template>
  <div id="app">
    <nav class="navbar navbar-inverse">
      <div class="container-fluid">
        <div class="navbar-header">
          <a class="navbar-brand" href="#">Adinnet-UI</a>
        </div>
      </div>
    </nav>

    <div class="wrap">
      <div class="col-lg-3">
        <div class="list-group">
          <a href="#" 
          class="list-group-item" 
          :class="currentNav == nav?'active':''"
          @click="currentNav = nav"
          v-for="nav in navs">
          {{nav}}
        </a>
      </div>
    </div>
    <div class="col-lg-9">
      <!-- tab -->
      <div class="ad-tab" v-show="currentNav == 'tab'">
        <ad-tab :data="data.tab" ></ad-tab>
      </div>
      <!-- forms -->
      <div class="ad-forms" v-show="currentNav == 'form'">
        <ad-form :data="data.form"></ad-form>
      </div>
    </div>
  </div>

</div>
</template>

<script>
  import adTab from './components/tab.vue'
  import adForm from './components/form.vue'
  export default {
    name: 'app',
    components: {
      adTab, adForm
    },
    data () {
      return {
        currentNav: 'form',
        navs: ['tab','form'],
        data: {
          tab: {
            "全部": "全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部全部",
            "国内": "国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内国内",
            "国际": "国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际国际"
          },
          form: {
            action: '/api/login', //post地址
            labelSize: 2,
            fields: {
              username: {
                label: '用户名',
                placeholder: '请输入用户名',
                type: 'text',
                value: 'aaa'
              },
              password: {
                label: '密码',
                placeholder: '请输入密码',
                type: 'password',
                value: '111'
              }

            }
          }
        }
      }
    },
    metheds: {
      
    }
  }
</script>

<style lang="scss">

</style>
