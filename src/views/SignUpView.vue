<script setup>
import { RouterLink } from 'vue-router'
import SideComponent from '@/components/Side.vue'
import EmailInput from '@/components/EmailInput.vue'
import PasswordInput from '@/components/PasswordInput.vue'
import NicknameInput from '@/components/NicknameInput.vue'
</script>

<template>
  <!-- sign up -->
  <div id="signUpPage" class="bg-yellow">
    <div class="conatiner signUpPage vhContainer">
      <SideComponent />
      <div>
        <form class="formControls" action="index.html">
          <h2 class="formControls_txt">註冊帳號</h2>
          <EmailInput />
          <NicknameInput />
          <PasswordInput label-name="密碼" placeholder="請輸入密碼"/>
          <PasswordInput label-name="再次輸入密碼" placeholder="請再次輸入密碼"/>
          <input
            class="formControls_btnSubmit"
            type="button"
            onclick="javascript:location.href='#todoListPage'"
            value="註冊帳號"
          />
          <RouterLink class="formControls_btnLink" to="/">登入</RouterLink>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
