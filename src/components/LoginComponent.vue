<template>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-md-6">
        <div class="card">
          <div class="card-header">登入</div>
          <div class="card-body">
            <form @submit.prevent="loginUser">
              <div class="form-group">
                <label>電話號碼</label>
                <input v-model="user.phoneNumber" class="form-control" type="phoneNumber" placeholder="請輸入電話號碼" />
              </div>
              <div class="form-group">
                <label>密碼</label>
                <input v-model="user.password" class="form-control" type="password" placeholder="請輸入密碼" />
              </div>
              <button type="submit" class="btn btn-primary">登入</button>
            </form>
            <div class="mt-3">
              <span>還沒註冊? <router-link to="/register">註冊帳號</router-link></span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import AuthService from '../services/AuthService';

export default {
  data() {
    return {
      user: {
        phoneNumber: '',
        password: ''
      }
    };
  },
  methods: {
    loginUser() {
      AuthService.login(this.user).then(response => {
        console.log(response.data);
      });
    }
  }
};
</script>