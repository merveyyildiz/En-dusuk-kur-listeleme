<template>
  <div id="lowest-rate">
    <div class="container mt-5">
      <div
        class="d-flex flex-column  align-items-center justify-content-center">
        <h4>Cheapest Rate</h4>
        <h6>{{ symbol }} {{ lowExchange }}</h6>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'LowestRate',
  data: () => ({
    veri: [],
    lowExchange: 0,
    symbol: ' ',
  }),
  mounted() {
    axios
      .get('http://www.mocky.io/v2/5a74519d2d0000430bfe0fa0')
      .then((response) => {
        console.log(response.data.result);
        this.veri = response.data.result;
        this.lowExchange = this.veri[0].amount;
        this.symbol = this.veri[0].symbol;
        for (let i = 0; i < this.veri.length; i++) {
          if (this.veri[i].amount < this.lowExchange) {
            this.symbol = this.veri[i].symbol;
            this.lowExchange = this.veri[i].amount;
          }
        }
      })
      .catch((error) => console.log(error));
  },
};
</script>
<style></style>
