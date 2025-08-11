<script setup>
import { RouterLink } from 'vue-router'
import SideComponent from '@/components/Side.vue'
import EmailInput from '@/components/EmailInput.vue'
import PasswordInput from '@/components/PasswordInput.vue'

</script>

<template>
  <!-- login_page -->
  <div id="loginPage" class="bg-yellow">
    <div class="conatiner loginPage vhContainer">
      <SideComponent />
      <div>
        <form class="formControls" action="index.html">
          <h2 class="formControls_txt">最實用的線上代辦事項服務</h2>
          <EmailInput />
          <PasswordInput label-name="密碼" placeholder="請輸入密碼"/>
          <input
            class="formControls_btnSubmit"
            type="button"
            onclick="javascript:location.href='#todoListPage'"
            value="登入"
          />
          <RouterLink class="formControls_btnLink" to="/sign-up">註冊帳號</RouterLink>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>
