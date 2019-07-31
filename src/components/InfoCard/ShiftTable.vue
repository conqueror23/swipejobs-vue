<template>
  <div>
    <h3>If you take this job you are agreeing to work ALL DAYS</h3>
    <div v-for="day in weekshift">
      <p class="gray-font">{{day}}</p>
    </div>
  </div>
</template>

<script>
import moment, { weekdays } from "moment";
import moment_timezone from "moment-timezone";

export default {
  name: "shiftTables",
  props: ["formatDate"],
  computed: {
    weekshift: function() {
      let weekshift = [];
      this.formatDate.filter((value, key) => {
        if (key < 5) {
          let result = value
            .tz("America/Los_Angeles")
            .format("ddd, MMM D  LT  z");
          weekshift = [...weekshift, result];
        }
      });
      return weekshift;
    }
  }
};
</script>

<style>
</style>
