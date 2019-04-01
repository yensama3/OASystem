<template>
  <div class="Login">
		
    <el-form :model="loginForm" status-icon :rules="rules" ref="loginForm" label-width="100px" class="demo-ruleForm">
			<h1 class="title">OA系统登陆</h1>
  <el-form-item label="用户名" prop="username">
    <el-input type="text" v-model="loginForm.username" autocomplete="off"></el-input>
  </el-form-item>
  <el-form-item label="密码" prop="pass">
    <el-input type="password" v-model="loginForm.pass" autocomplete="off"></el-input>
  </el-form-item>
  
  <el-form-item>
    <el-button type="primary" @click="submitForm('loginForm')">提交</el-button>
    
  </el-form-item>
</el-form>
    
  </div>
</template>

<script>
  export default {
    data() {
      var checkUsername = (rule, value, callback) => {
        if (!value) {
          return callback(new Error('用户名不能为空'));
        }
        setTimeout(() => {
         
            
              callback();
            
          
        }, 1000);
      };
      var validatePass = (rule, value, callback) => {
        if (value === '') {
          callback(new Error('请输入密码'));
        } else {
          
          callback();
        }
      };
      
      return {
        loginForm: {
          pass: '',
          checkPass: '',
          age: ''
        },
        rules: {
          pass: [
            { validator: validatePass, trigger: 'blur' }
          ],
          
          username: [
            { validator: checkUsername, trigger: 'blur' }
          ]
        }
      };
    },
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit!');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
html,body,#app,.Login{
	height: 100%;
}
.Login{
	
	display: flex;
	align-items: center;
	justify-content: center;
	
}
.Login .el-form{
	width: 400px;
	border: 1px solid #ccc;
	border-radius: 4px;
	padding: 40px 45px 10px 30px;
}
.Login .title{
	width: 100%;
	margin: 10px 170px 45px  ;
}

</style>
