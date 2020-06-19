<template>
  <div class="home">
    <h2>登录</h2>
    <img alt="Vue logo" src="../assets/logo.png">
    <div align="center" style="margin-left: -70px;">
      <el-form ref="form" :model="form" :rules="rules" label-width="100px">
        <el-form-item size="small" label="电话" prop="phone" style="width: 300px;">
          <el-input v-model="form.phone" prefix-icon="el-icon-user-solid" placeholder="请输入手机号"></el-input>
        </el-form-item>
        <el-form-item size="small" label="密码" prop="pwd" style="width: 300px;">
          <el-input v-model="form.pwd" prefix-icon="el-icon-s-tools" placeholder="请输入密码" show-password></el-input>
        </el-form-item>
        <el-form-item size="small">
          <el-button @click="submitForm('form')">登录</el-button>
          <el-button @click="resetForm('form')">重置</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'


export default {
  data() {
    let reg = /^1[3|4|5|7|8][0-9]{9}$/
    var validatePhone = (rule, value, callback) => {
      if (!reg.test(value)) {
        callback(new Error('电话号码格式不正确'))
      } else {
        callback()
      }
    }
    var validatePwd = (rule, value, callback) => {
      var reg2= /(?!^(\d+|[a-zA-Z]+|[~!@#$%^&*?]+)$)^[\w~!@#$%^&*?]{6,12}$/
      if (!reg2.test(value)) {
        callback(new Error('密码应是6-12位数字、字母或字符！'))
      } else {
        callback()
      }
    }

    return {
      form: {
        phone: '',
        pwd: ''
      },
      rules: {
        phone: [
          { required: true, message: '请输入电话号码', trigger: 'blur' },
          { validator: validatePhone, trigger: 'blur' }
        ],
        pwd: [
          { required: true, message: '请输入密码', trigger: 'blur' },
          { validator: validatePwd, trigger: 'blur' }
        ]
      }
    };
  },
  methods: {
    submitForm(formName) {
      let _this = this;
      this.$refs[formName].validate((valid) => {
        if (valid) {
          //登陆成功
          // console.log(this.form.phone)
           var datas=this.form;
           console.info(datas)
           _this.$router.push('/Index');
        } else {
          //登录失败
          alert('登录失败');
          return false;
        }
      });
    },
    //重置
    resetForm(formName) {
      this.$refs[formName].resetFields();
    }
  }
};

</script>
