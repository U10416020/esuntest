<template>
  <div>
      <h3>登入</h3>
      用户名:<input type="text" v-model="loginForm.loginName" placeholder="请输入用户名"/>
      <br><br>
      密码： <input type="password" v-model="loginForm.password" placeholder="请输入密码"/>
      <br><br>
      <button>登入</button>
  </div>
</template>

<script>

  export default {
    name: 'LoginPage',
    data () {
      return {
        loginForm: {
          loginName: '',
          password: ''
        },
        responseResult: []
      }
    },
    methods: {
    }
  }
</script>