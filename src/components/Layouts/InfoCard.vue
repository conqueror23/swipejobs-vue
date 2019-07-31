<template>
  <b-card light tag="article" class="mb-6">
    <b-row>
      <b-col class="company-info">
        <b-card-img :src="this.company.logo"></b-card-img>
        <b-card-text>
          <h3>{{this.jobInfo.title}}</h3>
          <h4>{{this.company.name}}</h4>
          <p>${{hourRate}}/hour</p>
          <!-- use moment().unix() to get the mimimun and maximun day or just  -->
          <p>{{workPeriod}}</p>
        </b-card-text>
      </b-col>
    </b-row>
    <b-card-text>
      <ShiftTable :formatDate="this.formatDate" />
    </b-card-text>
    <hr />
    <b-card-text>
      <b-row>
        <b-col class="company-location">
          <Location v-bind:address="this.company.address" />
        </b-col>
      </b-row>
    </b-card-text>
    <hr />
    <b-card-text>
      <b-row>
        <b-col class="company-branch">
          <Branch
            v-bind:branch="this.jobInfo.branch"
            v-bind:branchPhoneNumber="this.jobInfo.branchPhoneNumber"
          />
        </b-col>
      </b-row>
    </b-card-text>
    <hr />
    <b-row>
      <b-col class="company-buttons">
        <b-button href="#" variant="primary">No THANKS</b-button>
        <b-button href="#" variant="primary">I`LL TAKE IT</b-button>
      </b-col>
    </b-row>
  </b-card>
</template>

<script>
import ShiftTable from "@/components/InfoCard/ShiftTable";
import Branch from "@/components/InfoCard/Branch";
import Location from "@/components/InfoCard/Location";
import moment from "moment";
import moment_timezone from "moment-timezone";

export default {
  name: "InfoCard",
  props: ["jobInfo"],
  components: {
    Branch,
    Location,
    ShiftTable,
    formattedDate: ""
  },
  data() {
    return {
      company: this.jobInfo.company,
      shifts: this.jobInfo.shifts
    };
  },
  computed: {
    hourRate: function() {
      let hourrate = this.jobInfo.wagePerHourInCents / 100;
      return hourrate.toFixed(2);
    },
    formatDate: function() {
      let formatedDate = this.jobInfo.shifts.map(value => {
        //get the weekdays
        let output = moment(value.startDate)
          .tz("America/Los_Angeles")
          .add(18, "h");
        return output;
      });
      return formatedDate;
    },
    workPeriod: function() {
      let period = this.formatDate[0].format("ddd,  MMM D");
      let length = this.formatDate.length - 1;
      let lastDay = this.formatDate[length].format("ddd,  MMM D");
      return period + " - " + lastDay;
    }
  }
};
</script>

<style>
b-card img {
  width: 20%;
  height: 20%;
}
.company-info {
  display: flex;
}
.company-info .card-text {
  margin-left: 2em;
}
.company-buttons {
  display: inline-flex;
  justify-content: space-between;
}
</style>
