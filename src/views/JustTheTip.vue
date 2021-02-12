<template>
  <div class="container">
    <b-card>
      <div>How much is your bill?</div>
      <b-form-input v-model="bill" placeholder="Enter your bill"></b-form-input>
      <!-- <div class="mt-2">Value: {{ bill }}</div> -->
      <div>
        <div class="service">How was your service?</div>
        <b-dropdown id="dropdown-1" :text="serviceQual" class="m-md-2">
          <b-dropdown-item @click="myClick">5% - very poor </b-dropdown-item>
          <b-dropdown-item @click="myClick">10% - poor</b-dropdown-item>
          <b-dropdown-item @click="myClick">15% - ok </b-dropdown-item>
          <b-dropdown-item @click="myClick">20% - adaquate</b-dropdown-item>
          <b-dropdown-item @click="myClick">25% - good</b-dropdown-item>
          <b-dropdown-item @click="myClick">30% - great</b-dropdown-item>
        </b-dropdown>
        <div>How many people are sharing this bill?</div>
        <div>
          <b-form-input
            v-model="numberOfPeople"
            placeholder="Enter a number"
          ></b-form-input>
          <!-- <div class="mt-2">Value: {{ numberOfPeople }}</div> -->
        </div>
        <div>
          <b-button @click="percentage">Calculate</b-button>
          <div class="tip"><span v-if="hasTip">$</span>{{ this.tip }}</div>
        </div>
      </div>
    </b-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      bill: "",
      serviceQual: "Choose an Option",
      numberOfPeople: "",
      tip: "",
    };
  },
  computed: {
    hasTip() {
      return this.tip !== "";
    },
  },
  methods: {
    myClick(j) {
      console.log("Ass", j);
      console.log(j.srcElement.innerHTML);
      let p = `0.${j.srcElement.innerHTML.split("%")[0]}`;
      console.log(parseFloat(p));
      this.serviceQual = p;
    },
    percentage() {
      let n =
        (parseFloat(this.bill) * parseFloat(this.serviceQual)) /
        parseInt(this.numberOfPeople);
      n = Math.round(n * 100) / 100;
      console.log(n);
      this.tip = n.toFixed(2);
    },
  },
  mounted() {
    this.$root.$on("click", (bvEvent) => {
      console.log("Dropdown is about to be shown", bvEvent);
    });
  },
};
</script>

<style>
.container {
  max-width: 487px;
}
.form-control {
  text-align: center;
  display: block;
  width: 77%;
  height: calc(1.5em + 0.75rem + 2px);
  padding: 0.375rem 3.75rem;
  font-size: 1rem;
  font-weight: 400;
  line-height: 1.5;
  color: #495057;
  background-color: #fff;
  background-clip: padding-box;
  border: -5px solid #ced4da;
  border-radius: 0.25rem;
  transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
  margin-left: 50px;
  margin-top: 9px;
}

.mt-2,
.my-2 {
  margin-top: 0.5rem !important;
  margin-bottom: 15px;
}
.tip {
  padding-top: 10px;
}
.btn {
  margin-top: 8px;
}
.service {
  margin-bottom: -10px;
  margin-top: 10px;
}
</style>