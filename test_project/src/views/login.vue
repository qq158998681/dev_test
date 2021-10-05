<template>
  <div class="pt">
    <h1>欢迎使用测试开发平台</h1>

    <el-form :rules="rules" :model="form" label-width="120px" validate-on-rule-change ref="loginForm" class="input-text">
      <el-form-item label="账号" prop="usr" >
        <el-input v-model="form.usr" placeholder="请输入您的账号" clearable />
      </el-form-item>

      <el-form-item label="密码" prop="psw" class="input-text">
        <el-input
          v-model="form.psw"
          placeholder="请输入您的密码"
          clearable
          show-password
        />
      </el-form-item>

      <el-form-item>
        <el-button type="primary" round>登录</el-button>
        <el-button round @click="clearText">重置</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
import { ref, reactive } from "vue";
export default {
  name: "login",
  setup() {
    const loginForm = ref(null)
    const form = reactive({
      usr: "",
      psw: ""
    })
    const rules = {
      usr: [
        {
          required: true,
          message: '用户名不能为空',
          trigger: 'blur',
        },
        {
          min: 6,
          max: 12,
          message: '用户名长度必须在6到12位之间',
          trigger: 'blur',
        },
      ],
      psw: [
        {
          required: true,
          message: '密码不能为空',
          trigger: 'blur',
        }
      ]
  }

    function clearText() {
      (form.usr = ""), (form.psw = "")

    }

    return {
      form,
      clearText,
      rules,
      loginForm
    }
  },
}

</script>

