<template>
 <div class="login">
<el-form class="login-form" label-position="left" label-width="80px" :model="formData">
  <h2>用户登录</h2>
  <el-form-item label="用户名">
    <el-input v-model="formData.username"></el-input>
  </el-form-item>
  <el-form-item type="password" label="密码">
    <el-input v-model="formData.password"></el-input>
  </el-form-item>
  <el-form-item>
    <el-button @click ="handleLogin" type="primary"  class = "btn">登录</el-button>
   
  </el-form-item>
</el-form>
 </div>
</template>

<script>
import axios from 'axios'
 export default {
 data(){
     return{
         formData:{
             username:'',
             password:''
         }
     }
 },
 methods:{
   handleLogin(){
     axios
      .post('http://localhost:8888/api/private/v1/login',this.formData)
      .then((response)=>{
        console.log(response);
        var status =response.data.meta.status;
        var msg =response.data.meta.msg;
        var token = response.data.data.token;
        if(status ===200){
         this.$message({
          message: msg,
          type: 'success'
        });
        SessionStorage.setItem('token',token); 
        }else{
          this.$message.error(msg);
        }
        // 登陆成功
        //提示
        //记录token
        //跳转到首页
      })
      .catch((err)=>{
        console.log(err);
      })
   }
 },
   components: {

   }
 }
</script>

<style scoped>
/* 加scoped 解决命名冲突，给当前页面标签添加一个data-v-xx的属性标识，当前页面值为当前元素服务 */
.login{
  background-color:#324152;
  height:100%;
  display:flex;
  justify-content:center;
  align-items:center;


}
.login-form{
  background-color:#fff;
  width:500px;
  height:300px;
  padding:30px;
  border-radius:5px;
  /* text-align: left; */
  /* display: inline-block */
}
.btn{
  width:100%;
}
 
</style>
