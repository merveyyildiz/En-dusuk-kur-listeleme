<template>
  <div id="login" class="mt-5">
    <div class="m-5">
      <div class="col-lg-8  col-md-8 col-sm-10  centered my-box ">
        <h4 class="text-center text-muted">LOGIN</h4>
        <input
          type="text"
          placeholder="Username"
          class="form-control my-3"
          v-model="username"
        />
        <input
          type="password"
          placeholder="Password"
          class="form-control mb-3"
          v-model="password"
        />
        <button type="submit" class="btn btn-success btn-block" @click="login">
          Login
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'LoginPage',
  data: () => ({
    username: '',
    password: '',
    isLogin: false,
  }),
  methods: {
    login() {
      if (this.username.length != 0 && this.password.length != 0) {
        (this.username = ''),
          (this.password = ''),
          this.$emit('LoginPage::isLogin', { isLogin: true });
      } else {
        alert('Lütfen boş bırakmayınız');
        this.isLogin = false;
      }
    },
  },
};
</script>
<style>
.btn {
  font-size: 20px;
}
.my-box {
  border: 1px solid lightblue;
  padding: 30px 20px;
  border-radius: 10px;
  box-shadow: 2px 2px #c2eafa;
}
</style>
