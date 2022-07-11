<template>
  <section>
    <SearchBar @selectG="searchGenere" @selectCantante="searchAuthor"  :Albumobj="searchSong" />
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
  import SingleSong from "./SingleSong.vue";
  import axios from "axios";
  import SearchBar from "./SearchBar.vue";
  export default {
    name: "SongComponent",
    components:{
    LoadingSong,
    SingleSong,
    SearchBar
},
    props:{
    },
    data(){
      return{
        apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
        arraysong: [],
        load: false,
        Genre:"",
        Author:"",
      }
    },
    computed:{
     searchSong(){
        if (this.Genre === "All" && this.Author === "All") {
          return this.arraysong;
        } else if (this.Genre !== "All" && this.Author === "All"){ 
          return this.arraysong.filter(word => {
            return word.genre.includes(this.Genre)         
          });
        } else if (this.Genre === "All" && this.Author !== "All"){ 
          return this.arraysong.filter(word => {
            return word.author.includes(this.Author)         
          });
        } else {
          return this.arraysong.filter(word => {
            return word.author.includes(this.Author) && word.genre.includes(this.Genre)       
          });
        }      
      },
    },
    mounted(){
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
      },
      searchGenre(world){
        console.log(world);
        this.Genre = world;
      },
        searchAuthor(world){
        this.valueAuthor = world;
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