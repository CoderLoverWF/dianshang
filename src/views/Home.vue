<template>
 <el-container class="container">
  <el-header class="header">   
    <el-row>
      <el-col :span="3">
        <img src="@/assets/logo.png" alt="">
      </el-col>
      <el-col :span="20">
        <div class="header-title">电商管理系统</div>
      </el-col>
      <el-col :span="1">
        <div class = "logo">
          <a @click.prevent = "logOut" href="#">退出</a>
        </div>
      </el-col>
    </el-row>
  </el-header>
  <el-container>
    <el-aside class="aside" width="200px">
      <!-- 设置只展开一项，高度el-menu100%
      开启路由 -->
      <el-menu
      unique-opened
      router
      style='height:100%'
      default-active="1"
      class="el-menu-vertical-demo"
     >
      <el-submenu index="1">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>用户管理</span>
        </template>
        <el-menu-item-group>
           
          <el-menu-item index="/users">
            <i class="el-icon-menu"></i>
            用户列表</el-menu-item>
        </el-menu-item-group>
     
      </el-submenu>
     <el-submenu index="2">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>权限管理</span>
        </template>
        <el-menu-item-group>
           
          <el-menu-item index="/roles">
            <i class="el-icon-menu"></i>
            角色列表</el-menu-item>
            <el-menu-item index="/limits">
            <i class="el-icon-menu"></i>
            权限列表</el-menu-item>
        </el-menu-item-group>
     
      </el-submenu>
      <el-submenu index="3">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>商品管理</span>
        </template>
        <el-menu-item-group>
           
          <el-menu-item index="3-1">
            <i class="el-icon-menu"></i>
            商品列表</el-menu-item>
            <el-menu-item index="3-2">
            <i class="el-icon-menu"></i>
            分类参数</el-menu-item>
            <el-menu-item index="3-3">
            <i class="el-icon-menu"></i>
            商品分类</el-menu-item>
        </el-menu-item-group>
     
      </el-submenu>
      <el-submenu index="4">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>订单列表</span>
        </template>
        <el-menu-item-group>
           
          <el-menu-item index="4-1">
            <i class="el-icon-menu"></i>
            订单列表</el-menu-item>
        </el-menu-item-group>
     
      </el-submenu>
      <el-submenu index="5">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>数据统计</span>
        </template>
        <el-menu-item-group>
           
          <el-menu-item index="5-1">
            <i class="el-icon-menu"></i>
            数据报表</el-menu-item>
        </el-menu-item-group>
     
      </el-submenu>
    </el-menu>
    </el-aside>
    <el-main class = "main">Main</el-main>
  </el-container>
</el-container>
</template>

<script>
 export default {
   beforeCreate(){
    //  判断是否登录
    var token = sessionStorage.getItem('token');
    if(!token){
      this.$message.warning('请先登录');
      this.$router.push('/login')
    }
   },
   components: {

   },
   methods:{
     logOut(){
      //  提示退出成功
      this.$message.success('退出成功');
      //清除token
      sessionStorage.clear();
      // 跳转到登录页码
      this.$router.push('/login')
     }
   }
 }
</script>

<style>
.container{
    height:100%;
}
.header{
    background-color:#b3c0d1;
    padding:0px;
}
.header .header-title{
    text-align:center;
    line-height:60px;
    color:white;
    font-size:30px;
    
}
.header .logo{
  line-height:60px;
  
}
.header .logo a{
  color:orange;
  text-decoration:none;
}
.aside{
    background-color:#d3dce6;
}
.main{
    background-color:#e9eef3;
    height:100%;
}
 ;
</style>
