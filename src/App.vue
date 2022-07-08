<template>
  <div id="app">
    <PageHeader />
      <main>
   <SongComponent />
  </main>
  </div>
 
</template>

<script>
import PageHeader from './components/PageHeader.vue';
import SongComponent from './components/SongComponent.vue';

export default {
  name: 'App',
  components: {
    PageHeader,
    SongComponent
},
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
