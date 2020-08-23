<template>
  <div id="table">
    <div class="container mt-5">
      <div
        class="d-flex flex-column  align-items-center justify-content-center"
      >
        <h4>EXCHANGE RATE</h4>
        <datatable
          class="border table table-striped col-md-4 mt-2 "
          :columns="columns"
          :data="veri"
        ></datatable>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Table',
  data: () => ({
    veri: [],
    columns: [
      { label: 'Symbol', field: 'symbol' },
      { label: 'Amount', field: 'amount' },
    ],
  }),
  mounted() {
    axios
      .get('http://www.mocky.io/v2/5a74519d2d0000430bfe0fa0')
      .then((response) => {
        this.veri = response.data.result;
      })
      .catch((error) => console.log(error));
  },
};
</script>
<style></style>
