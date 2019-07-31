<template>
  <div class="app">
    <NavBar />
    <ContentWraper />
  </div>
</template>

<script>
import NavBar from "@/components/Layouts/NavBar";
import ContentWraper from "@/components/Layouts/ContentWraper";
export default {
  name: "app",
  components: {
    NavBar,
    ContentWraper
  }
};
</script>

<style>
.app {
  display: flex;
  flex-direction: column;
}
.gray-font {
  color: #bdc3c7;
  font-weight: 600;
}
.bold {
  font-weight: bold;
}
@media screen and (min-width: 1024px){
  .card img{
    width: 60%!important;
  }
  @media screen and (max-width: 540px) and( min-width: 276px){
    .card img{
      width: 40%;
      height: 40%;

    }
    
  }
  
}

</style>
