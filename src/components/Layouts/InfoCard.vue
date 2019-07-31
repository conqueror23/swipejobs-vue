<template>
  <b-card light tag="article" class="mb-6">
    <b-row>
      <b-col  class="company-info">
        <b-card-img :src="this.company.logo" ></b-card-img>
        <b-card-text>
          <h3>{{this.jobInfo.title}}</h3>
          <h4>{{this.company.name}}</h4>
          <p>${{this.jobInfo.wagePerHourInCents/100}}/hour</p>
          <p>Display your shift infos here</p>
        </b-card-text>
      </b-col>
    </b-row>
    <hr />
    <b-card-text>
      <ShiftTable :shiftTable="this.jobInfo.shifts"/>
    </b-card-text>
    <hr />
    <b-card-text>
      <b-row>
        <b-col  class="company-location">
          <Location v-bind:address="this.company.address"/>
        </b-col>
      </b-row>
    </b-card-text>
    <hr />
    <b-card-text>
      <b-row>
        <b-col  class="company-branch">
          <Branch v-bind:branch="this.jobInfo.branch" v-bind:branchPhoneNumber="this.jobInfo.branchPhoneNumber"/>
        </b-col>
      </b-row>
    </b-card-text>
    <hr />
    <b-row>
      <b-col  class="company-buttons">
        {{psdtime}}
        <b-button href="#" variant="primary">No THANKS</b-button>
        <b-button href="#" variant="primary">I`LL TAKE IT</b-button>
      </b-col>
    </b-row>
  </b-card>
</template>

<script>
import ShiftTable from '@/components/InfoCard/ShiftTable'
import Branch from '@/components/InfoCard/Branch'
import Location from '@/components/InfoCard/Location'
export default {
  name: "InfoCard",
  props: ["jobInfo"],
  components:{
    Branch,
    Location,
    ShiftTable,
  },
  data() {
    return {
      company: this.jobInfo.company,
      shifts:this.jobInfo.shifts,
    };
  },
  computed:{
    psdtime:()=>{
      let timeTable = shifts[0];
      console.log(timeTable);

    }
  }
};
</script>

<style>
b-card img {
  width: 20%;
}
.company-info {
  display: flex;
}
.company-info .card-text {
  margin-left: 2em;
}
.company-buttons{
  display: inline-flex;
  justify-content: space-between;
}
</style>
