<template>
  <div id="location">
    <h3>Location</h3>
    <a href="#">{{address}}</a>
  </div>
</template>

<script>
export default {
  name: "location",
  props: ["address"]
};
</script>

<style>
#location a{
    font-size: 2em;
    text-decoration: underline;

}

</style>
