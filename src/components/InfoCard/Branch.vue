<template>
  <div>
    <h4>Branch</h4>
    <h4>{{branch}}</h4>
    <a href>{{branchPhoneNumber}}</a>
  </div>
</template>

<script>
export default {
  name: "branch",
  props: ["branch", "branchPhoneNumber"]
};
</script>

<style>
</style>
