<template>
  <div class="auth-container">
    <div class="login-container" v-if="!showRegister">
      <h2>登入</h2>
      <form @submit.prevent="login">
        <input type="text" v-model="loginUsername" placeholder="使用者名稱" required>
        <input type="password" v-model="loginPassword" placeholder="密碼" required>
        <button type="submit">登入</button>
      </form>
      <p v-if="loginErrorMessage" style="color: red;">{{ loginErrorMessage }}</p>
      <p @click="toggleForm" class="toggle-form">註冊新帳號</p>
    </div>

    <div class="register-container" v-if="showRegister">
      <h2>註冊</h2>
      <form @submit.prevent="register">
        <input type="text" v-model="registerUsername" placeholder="使用者名稱" required>
        <input type="password" v-model="registerPassword" placeholder="密碼" required>
        <button type="submit">註冊</button>
      </form>
      <p v-if="registerErrorMessage" style="color: red;">{{ registerErrorMessage }}</p>
      <p @click="toggleForm" class="toggle-form">返回登入</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loginUsername: '',
      loginPassword: '',
      loginErrorMessage: '',
      registerUsername: '',
      registerPassword: '',
      registerErrorMessage: '',
      showRegister: false,
    };
  },
  methods: {
    login() {
      if (this.loginUsername === 'admin' && this.loginPassword === '123456') {
        alert('登入成功！');
        this.loginErrorMessage = '';
      } else {
        this.loginErrorMessage = '使用者名稱或密碼錯誤！';
      }
    },
    register() {
      if (this.registerUsername && this.registerPassword) {
        alert('註冊成功！');
        this.registerErrorMessage = '';
        this.showRegister = false; // 註冊成功後返回登入
      } else {
        this.registerErrorMessage = '請填寫所有欄位！';
      }
    },
    toggleForm() {
      this.showRegister = !this.showRegister;
      this.loginErrorMessage = '';
      this.registerErrorMessage = '';
    }
  }
};
</script>

<style>
.auth-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.login-container,
.register-container {
  background: white;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  width: 300px;
  margin: 20px 0;
}
input {
  width: 100%;
  padding: 10px;
  margin: 10px 0;
  border: 1px solid #ccc;
  border-radius: 3px;
  box-sizing: border-box; /* 確保 padding 不影響寬度 */
}
input:not(:last-child) {
  margin-bottom: 15px; /* 增加每個 input 之間的間距 */
}
button {
  width: 100%;
  padding: 10px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 3px;
  cursor: pointer;
}
button:hover {
  background-color: #0056b3;
}
.toggle-form {
  color: #007bff;
  cursor: pointer;
  text-decoration: underline;
}
</style>