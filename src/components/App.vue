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
  font-weight: 500;
}
.bold {
  font-weight: bold;
}
/* .card img {
  width: 70%;
} */
@media screen and (max-width: 270px) {
  .card img {
    height: 70%;
  }

  h3 {
    font-size: 0.6em;
  }
  h4,
  h5 {
    font-size: 0.4em;
  }
  p {
    font-size: 0.3em;
  }
}
@media screen and (max-width: 410px) and (min-width: 270px) {
  h3 {
    font-size: 1.5em;
  }
  h4,
  h5 {
    font-size: 1.3em;
  }
  p {
    font-size: 0.3em;
  }
}
@media screen and (max-width: 768px) and (min-width: 410px) {
  .card img {
    width: 60%;
  }
  h3 {
    font-size: 1.7em;
  }
  h4,
  h5 {
    font-size: 1.5em;
  }
  p {
    font-size: 0.5em;
  }
}

@media screen and (max-width: 1023px) and (min-width: 991px) {
  .card {
    display: flex;
    justify-content: space-around;
  }
  .card img {
    width: 80%;
  }
}
@media screen and (min-width: 1024px) {
  .card img {
    width: 60% !important;
  }
}
</style>
