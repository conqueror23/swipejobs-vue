<template>
  <div id="branch">
    <h4>Branch:</h4>
    <h4>{{branch}}</h4>
    <a href>
      <h3>{{branchPhoneNumber}}</h3>
    </a>
  </div>
</template>

<script>
export default {
  name: "branch",
  props: ["branch", "branchPhoneNumber"]
};
</script>

<style>
#branch a {
  text-decoration: underline;
}
</style>
