<template>
  <b-container>
    <b-card light tag="article" >
      <b-row id="company-info-row">
        <b-col class="company-info">
          <b-card-img :src="this.company.logo"></b-card-img>
        </b-col>
        <b-col >
          <b-card-text>
            <h4>{{this.jobInfo.title}}</h4>
            <h5 class="gray-font">{{this.company.name}}</h5>
            <h5 class="gray-font">${{hourRate}}/hour</h5>
            <h4 class="gray-font bold">{{workPeriod}}</h4>
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
          <a href="#">THANKS</a>
          <a href="#">I`LL TAKE IT</a>
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
  },
  data() {
    return {
      company: this.jobInfo.company,
    };
  },
  computed: {
    //calculate salary of this job in 2 decimals
    hourRate: function() {
      let hourRate = this.jobInfo.wagePerHourInCents / 100;
      return hourRate.toFixed(2);
    },
    // get the working period of currenty job
     workPeriod: function() {
      let firstDay = this.formatDate[0].format("ddd,  MMM D");
      let length = this.formatDate.length - 1;
      let lastDay = this.formatDate[length].format("ddd,  MMM D");
      return firstDay + " - " + lastDay;
    },
    // transfer date to pst time
    formatDate: function() {
      let formatedDate = this.jobInfo.shifts.map(value => {
        let output = moment(value.startDate)
          .tz("America/Los_Angeles")
          .add(18, "h");
        return output;
      });
      return formatedDate;
    },

  }
};
</script>

<style>

.company-info {
  display: flex;
  justify-content: space-evenly;
}
.company-info .card-text {
  margin-left: 10%;
}
.company-info h5 {
  line-height: 1em;
}

#company-info-row{
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
#company-info-row b-col{
  width: 50%;

}
.company-buttons {
  display: inline-flex;
  justify-content: space-evenly;
  padding: 1em 1em;
}
</style>
