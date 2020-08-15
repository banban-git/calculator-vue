<template>
  <div id="app" class="container">
  <h1>Form Example</h1>
  <div class="form-group">
    <label>Email [必須]</label>
    <input v-model="userInfo.email" type="email" class="form-control" placeholder="例) sample@example.com">
    <span v-show="!validateEmail" class="text-warning">正しいEmailを入力してください</span>
  </div>
  <div class="form-group">
    <label>Tel [必須]</label>
    <input v-model="userInfo.tel" type="text" class="form-control" placeholder="例) 0311112222">
    <span v-show="!validateTel" class="text-warning">Telは数値で入力してください</span>
  </div>
  <div class="form-group">
    <label>ユーザー名</label>
    <input v-model="userInfo.userName" type="text" class="form-control" placeholder="例) user-1">
    <span v-show="!validateUserName" class="text-warning">ユーザー名は半角英数字で入力してください</span>
  </div>
  <button :disabled="!validation" type="button" class="btn btn-info">Next</button>
</div>
</template>

<script>

export default {
  name: 'Calculator',
  data () {
    return {
      userInfo: {
        email: '',
        tel: '',
        userName: ''
      }
    }
  },
  computed: {
    validation () {
      alert('validation')
      alert('this.validateTel:' + this.validateTel)
      alert('this.validateEmail:' + this.validateEmail)
      alert('this.validateUserName:' + this.validateUserName)
      return (this.validateTel &&
              this.validateEmail &&
              this.validateUserName)
    },
    validateTel () {
      alert('validateTel')
      var pattern = /^\d+$/ // 1文字以上の整数のみ許容
      return pattern.test(this.userInfo.tel.trim())
    },
    validateEmail () {
      alert('validateEmail')
      var pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
      return pattern.test(this.userInfo.email)
    },
    validateUserName () {
      alert('validateUserName')
      if (this.userInfo.userName.length === 0) {
        return true
      } else {
        var pattern = /^\w+$/ // 大文字小文字英数字、アンダースコアのみ許容
        return pattern.test(this.userInfo.userName)
      }
    }
  }
}
</script>

<style scoped>
</style>
