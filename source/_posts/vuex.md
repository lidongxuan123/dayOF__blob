---
title: vuex的使用方式
date: 2020-03-20 15:50:12
tags: vuex的使用方式
categories: vuex使用
---
# store/index.js
```
import Vue from "vue";
import Vuex from "vuex";
Vue.use(Vuex);
export default new Vuex.Store({
  state: {
    name: "小明",
  },
  getters: {
    getName(state){
      return state.name
    }
  },
  mutations: {
    saveName(state, name){
      state.name = name
    }
  },
  actions: {
    saveName: ({ commit }) => commit('saveName'),
  },
  modules: {}
});
```
1. 第一种使用方式
```
<template>
  <div class="home">
    {{value}}  
    使用this.$store的方式用来修改vuex里的数据
  </div>
</template>
<script>
  export default {
    name: "Home",
    data() {
      return {
        value: this.$store.getters.getName
      }
    },
    mounted() {
      console.log(this.$store.getters.getName)
      this.$store.commit('saveName',"小兰")
    },
  };
</script>
```
2. 第二种使用方式
```
<template>
  <div class="home">
    <button @click="aa">aaaa</button>
    {{value}}
  </div>
</template>
<script>
  import {mapGetters, mapMutations ,mapActions} from 'vuex'
  export default {
    name: "Home",
    data() {
      return {
        value:  this.getName()
      }
    },
    mounted() {
    },
    methods: {
      ...mapGetters([
        'getName'
      ]),
      ...mapMutations([
        'saveName'
      ]),
      aa(){
        this.saveName("小兰")
        this.value = this.getName()
      }
    }
  };
</script>
```