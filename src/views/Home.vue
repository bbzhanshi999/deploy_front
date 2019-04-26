<template>
  <div>
    <form>
      用戶名：
      <input type="text" name="username" v-model="username">
      <br>密码：
      <input type="password" name="password" v-model="password">
      <br>
      <button @click.prevent="login">提交</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "home",
  data() {
    return {
      username: "",
      password: ""
    };
  },
  methods: {
    login() {
      axios
        .post("/api/login", {
          username: this.username,
          password: this.password
        })
        .then(function(res) {
          this.$router.push({ name: '/roles', params: { username: res.data.username } })
        })
        .catch(function(error) {
          alert(error)
        });
    }
  }
};
</script>
