<!--
 * @Author: your name
 * @Date: 2020-02-23 18:16:10
 * @LastEditTime: 2020-02-25 11:58:44
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \portalSite_UI_vue\src\layout\components\horizontalMenu\index.vue
 -->
<template>
    <div class="navbar" >
      <logo></logo>
      <!------------导航菜单---------------->
     
        <el-menu
        mode="horizontal"
        background-color="#fff"
        text-color="#000"
        active-text-color="rgb(52, 113, 176)"
        :unique-opened="true"
        :default-active="activeMenu"
        router
      >
         <nav-menu v-for="route in permission_routes" :key="route.path" :item="route" :base-path="route.path" ></nav-menu>
        </el-menu>
    
        
    
    <div class="header-content" >
      <!--搜索框--->
      <el-input v-model="fastsearch"  class="header-search" placeholder="请输入" >
          <template slot="append" >
              <i class="el-icon-search" style="color: #fff" @click="searchEnter"  ></i>
           </template>
        </el-input>
    </div>
        
    </div>
</template>

<script>
import {mapGetters} from 'vuex'
import NavMenu from './NavMenu'
import Item from './Item'
import Logo from './Logo'
import Login from '@/views/login/login.vue'

export default {
    data(){
        return{
          onlyOneChild:[],
          searchVlaue:null,
          fastsearch:null,
        }
    },
    components:{
        Item,
        NavMenu,
        Logo,
        Login
    },
    computed: {
      ...mapGetters([
         'permission_routes',
         'user_name'
       ]),
        activeMenu(){
          const route = this.$route
          const { meta,path } = route
          if(meta.activeMenu){
            return meta.activeMenu
          }
          return path
        },
        loginStatue(){
       
          if(this.$store.getters.login_status){
            return this.$store.getters.login_status
          }
          else{
            return false
          }
        }
    },
    methods:{
      // 显示登录框
      showLogin(){
        this.$refs['login'].handleShowDialog()
      },
      //跳转
      searchEnter(){
        if(this.fastsearch === null || this.fastsearch === ""){
          this.$message.info("请输入搜索内容")
          return ;
        }else{
          this.$router.push({path:'/search',query:{fastsearch:this.fastsearch}})
        }
        
        /*   this.bus.$emit('searchData',{fastsearch:this.fastsearch}); */
          // 定时让其目标组件加载完成
        /*   setTimeout(()=>{
            this.bus.$emit('searchData',{fastsearch:this.fastsearch});
          },1000) */
        
      },
      //用户下拉菜单指令
      handleCommand(value){
        switch(value){
          case 'a':{
            
          };break;
          case 'b':{
            this.$store.dispatch('user/logout').then(()=>{
              this.$message({
                message:'退出成功',
                type:'success'
              })
            })
          }
        }
      }
    },
    mounted(){
    }
}

</script>
<style scoped>
body {
  background-color: #ffffff; /* 白色背景色 */
}
</style>
