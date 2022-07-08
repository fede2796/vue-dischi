<template>
  <div id="app">
    <PageHeader />
  </div>
  <main>
    {{arraysong}}
  </main>
</template>

<script>
import PageHeader from './components/PageHeader.vue';
import axios from "axios";
import { response } from 'express';

export default {
  name: 'App',
  components: {
    PageHeader, 

},
  data() {
    return{
      apiUrl:"https://flynn.boolean.careers/exercises/api/array/music",
      arraysong: [],
    }
},
  mounted(){
    this.ApiSongList();
  },
  methods:{
    ApiSongList(){
      axios.get(this.apiUrl).then(response =>{
        console.log(response);
        this.arraysong = response.data.response;
      })
      .catch((err)=>{
        console.log(err);
      })
    }
  }
}
</script>

<style lang="scss">
@import "./style/common";
@import "@/style/variables.scss";
main{
    height: calc(100vh - 60px);
    width: 100%;
    background-color: $main-bg-color;
  }
</style>
