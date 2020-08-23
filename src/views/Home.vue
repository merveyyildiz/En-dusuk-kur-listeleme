<template>
  <div class="home">
    <router-view v-if="isLoggedIn"></router-view>
    <Table v-if="isLoggedIn" />
    <template v-else>
     <div class="container">
      <div class="row">
        <div class="col-md-4 mt-5"><LowestRate /></div>
        <div class="col-md-8">
          <LoginPage @LoginPage::isLogin="handleLoginResult" />
        </div>
      </div>
      </div>
    </template>
  </div>
</template>

<script>
import LoginPage from '../components/LoginPage';
import Table from '../components/Table';
import LowestRate from '../components/LowestRate';
export default {
  name: 'Home',
  data: () => ({
    userIsLoggedIn: false,
  }),
  components: {
    LoginPage,
    Table,
    LowestRate,
  },
  computed: {
    isLoggedIn() {
      return this.userIsLoggedIn;
    },
  },
  methods: {
    handleLoginResult({ isLogin }) {
      this.userIsLoggedIn = isLogin;
    },
  },
};
</script>
