<template>
<header>
    <!-- Header Logo -->
    <div class="logo">
        <img src="../assets/img/spotify.svg" alt="Spotify">
    </div>
</header>
</template>

<script>
export default{
    name:"PageHeader"
}
</script>

<style lang="scss" scoped>
 @import "@/style/variables.scss";
header{
     background-color: $bg-color-secondary;

      .logo{
      height: 60px;    
      display: flex;
      align-items: center;
      padding: 0 17px;
      
      img{
        width: 40px;
        height: 40px;
        color: red;      
      }
    }
}
</style>

