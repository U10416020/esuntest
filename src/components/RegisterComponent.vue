<template>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-md-6">
        <div class="card">
          <div class="card-header">註冊帳號</div>
          <div class="card-body">
            <form @submit.prevent="registerUser">
              <div class="form-group">
                <label>姓名</label>
                <input v-model="user.userName" class="form-control" type="text" placeholder="請輸入姓名" />
              </div>
              <div class="form-group">
                <label>電話號碼</label>
                <input v-model="user.phoneNumber" class="form-control" type="text" placeholder="請輸入電話號碼" />
              </div>
              <div class="form-group">
                <label>密碼</label>
                <input v-model="user.password" class="form-control" type="password" placeholder="請輸入密碼" />
              </div>
              <button type="submit" class="btn btn-primary">註冊</button>
            </form>
            <div class="mt-3">
              <span>已經有帳號? <router-link to="/login">登入</router-link></span>
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
        userName: '',
        phoneNumber: '',
        password: ''
      }
    };
  },
  methods: {
    registerUser() {
      AuthService.register(this.user).then(response => {
        console.log(response.data);
      });
    }
  }
};
</script>