<template>
  <div id="content">
    <div  v-for="job in JobsInfo">
      <InfoCard v-bind:jobInfo="job" />
    </div>
  </div>
</template>

<script>
import JobsInfo from "@/assets/data";
import InfoCard from "@/components/Layouts/InfoCard";
export default {
  name: "Content",
  components: {
    InfoCard
  },
  data() {
    return {
      JobsInfo
    };
  }
};
</script>

<style>
#content {
  background: #bdc3c7;
}
</style>
