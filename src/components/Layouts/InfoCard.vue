<template>
  <b-container>

  <b-card light tag="article" class="mb-6">
    <b-row>
      <b-col class="company-info">
        <b-card-img :src="this.company.logo" ></b-card-img>
      </b-col>
      <b-col>
        <b-card-text>
          <h4>{{this.jobInfo.title}}</h4>
          <h5 class="gray-font">{{this.company.name}}</h5>
          <h5 class="gray-font">${{hourRate}}/hour</h5>
          <!-- use moment().unix() to get the mimimun and maximun day or just  -->
          <h4 class="gray-font">{{workPeriod}}</h4>
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
        <a href='#'> THANKS</a>
        <a href='#'>I`LL TAKE IT</a>
      </b-col>
    </b-row>
  </b-card>
  </b-container>
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
.card {
  margin: 0 1em !important;
  display: flex;
  flex-direction: column;
}
.card img{
  width: 100%;
}
.company-info {
  display: flex;
  justify-content: space-evenly;
}
.company-info .card-text {
  margin-left: 2em;
}
.company-buttons {
  display: inline-flex;
  justify-content: space-evenly;
  padding: 1em 1em;
}
</style>
