<template>
  <div>
    <h3>If you take this job you are agreeing to work ALL DAYS.</h3>
    <table id="shift-table"  v-for="day in weekshift">
      <tr>
        <td v-for="attr in day.split(' ')" >
          <p id="week-shift" class="gray-font">{{attr}}</p>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>

export default {
  name: "shiftTables",
  props: ["formatDate"],
  computed: {
    // only display following 5 days of work start time
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
#shift-table {
  margin: 0 0.2em;
}
#shift-table table td {
  height: 0.7em;
  padding: 0.2em;
  align-content: right;
  text-align: right;
}

#week-shift {
  line-height: 0.7em;
  font-size: 1.2em;
}
</style>
