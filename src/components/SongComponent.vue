<template>
  <section>
    <div class="container">
      <div v-if="load" class="row row-cols-5">
        <div class="col gy-3" v-for="song,index in arraysong" :key="index">
            <SingleSong :singleSong="song" />
        </div>
      </div>
       <LoadingSong v-else />
    </div>
  </section>
</template>

<script>
  import LoadingSong from "./LoadingSong.vue";
  import SingleSong from "./SingleSong.vue"
  import axios from "axios";
  export default {
    name: "SongComponent",
    components:{
        LoadingSong,
        SingleSong
    },
    props:{
    },
    data(){
      return{
        apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
        arraysong: [],
        load: false,
      }
    },
    created(){
      this.ApiSong();
    },
    methods:{
      ApiSong(){
        axios.get(this.apiUrl).then(response => {
          console.log(response.data.response)
          this.arraysong = response.data.response;
        })
        .catch((err) =>{
          // has failed
          console.log(err);    
        })
        this.load = true;
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import "@/style/variables.scss";
  section{
    width: 80%;
    margin: 0px auto;
    padding: 60px 0;
  }
</style>