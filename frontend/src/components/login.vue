<template>
    <div class="login">
      <el-form label-width="80px">
        <el-form-item label="用户名">
          <el-input v-model="form.username"></el-input>
        </el-form-item>
        <el-form-item label="密码">
          <el-input v-model="form.password" type="password"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="onLogin">登录</el-button>
          <el-button>取消</el-button>
        </el-form-item>
      </el-form>
    </div>
</template>

<script>
import axios from 'axios';
export default {
  name: "login",
  data() {
    return {
      form: {
        username: null,
        password: null
      }
    }
  },
  methods: {
    onLogin() {
      axios.post('http://127.0.0.1:8000/api/v1/auth/',this.form,{withCredentials:true}).then((res)=> {
        console.log(res);
        this.$router.go({path:'/'});
      });
    }
  }
}
</script>

<style scoped>
.login {
  width: 50%;
  margin: 0 auto;
}
</style>