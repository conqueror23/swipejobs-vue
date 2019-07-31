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
.card img {
  width: 70%;
}
@media screen and (max-width: 768px) and (min-width: 410px) {
  .card img {
    height: 40%;
  }
}
@media screen and (max-width: 410px) and (min-width: 270px) {
  .card img {
    display: none;
  }
}
@media screen and (min-width: 1024px) {
  .card {
    flex: 50%;
  }
  .card img {
    width: 50% !important;
  }
  @media screen and (max-width: 1023px) and (min-width: 991px) {
    .card {
      display: flex;
      justify-content: space-around;
    }
  }
}
</style>
