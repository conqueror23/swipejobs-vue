<template>
  <div id="location">
    <h3>Location</h3>
    <a href="#" ><h3>
        {{address}}
        </h3>
        </a>
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
    text-decoration: underline;

}

</style>
