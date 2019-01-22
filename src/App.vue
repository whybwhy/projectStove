<template>
  <div id="app">
        <Header></Header>
        <Upload v-on:uploadImage="uploadImage"></Upload>
        <List v-bind:propsImageList="imageList" v-on:removeAllItem="removeAllItem" v-on:removeItem="removeItem"></List>
        <Footer></Footer>
  </div>
</template>

<script>

import Vue from 'vue'
import BootstrapVue from 'bootstrap-vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
import Header from './components/Header'
import Upload from './components/Upload'
import List from './components/List'
import Footer from './components/Footer'

Vue.use(BootstrapVue)

export default {
  data () {
    return {
      imageList: [],
      prefix: 'sg_'
    }
  },
  components: {
    'Header': Header,
    'Upload': Upload,
    'List': List,
    'Footer': Footer
  },
  methods: {
    uploadImage (dataUrl) {
      let key = this.prefix + new Date().getTime()
      localStorage.setItem(key, dataUrl)
      this.setData(key, dataUrl)
    },
    removeItem (key, index) {
      localStorage.removeItem(key)
      this.imageList.splice(index, 1)
    },
    removeAllItem () {
      for (let i = 0; i < localStorage.length; i++) {
        if (localStorage.key(i).includes(this.prefix)) {
          localStorage.clear()
        }
      }
      this.imageList = []
    },
    setData (key, value) {
      this.imageList.push({ key: key, value: value })
    }
  },
  created () {
    for (let i = 0; i < localStorage.length; i++) {
      if (localStorage.key(i).startsWith(this.prefix)) {
        this.setData(localStorage.key(i), localStorage.getItem(localStorage.key(i)))
      }
    }
  }
}
</script>

<style>

</style>
