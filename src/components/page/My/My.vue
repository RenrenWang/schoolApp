<template>
  <div class="my">
         <NavBar    fixed="true" title="我的" />
         <main class="main">
                 <ul class="me-list">
                      <li  class="me-list-first">
                          <router-link :to='username?"/my":"/login"'>
                               <div class="item-l">
                                     <img src="../../../assets/images/userimage.png" class="item-icon"/>
                                     <span v-if="username">{{username}}</span>
                                     <span v-else>点击登录</span>
                               </div>
                               <div class="item-r">
                                   <span class="iconfont icon-fangxiang"></span>
                               </div>
                          </router-link>
                       </li>
                                              
                       <li>
                          <router-link to="/instr">
                               <div class="item-l">
                                     <span class="iconfont icon-fangxiang item-icon"></span>
                                     <span>应用介绍</span>
                               </div>
                               <div class="item-r">
                                   <span class="iconfont icon-fangxiang"></span>
                               </div>
                          </router-link>
                       </li>
                       
                       <li>
                          <router-link to="/cusinfo">
                               <div class="item-l">
                                     <span class="iconfont icon-fangxiang item-icon"></span>
                                     <span>房产客服</span>
                               </div>
                               <div class="item-r">
                                   <span class="iconfont icon-fangxiang"></span>
                               </div>
                          </router-link>
                       </li>
                       
                        <li>
                          <router-link to="/share">
                               <div class="item-l">
                                      <span class="iconfont icon-fenxiang item-icon"></span>
                                     <span>应用分享</span>
                               </div>
                               <div class="item-r">
                                   <span class="iconfont icon-fangxiang"></span>
                               </div>
                       </router-link>
                       </li>
                       
                       <li>
                          <router-link to="/about">
                               <div class="item-l">
                                     <span class="iconfont icon-guanyuwomen item-icon"></span>
                                     <span>技术支持</span>
                               </div>
                               <div class="item-r">
                                   <span class="iconfont icon-fangxiang"></span>
                               </div>
                          </router-link>
                       </li>
                       
                      <!-- <li>
                          <router-link to="/version">
                               <div class="item-l">
                                     <span class="iconfont icon-chakan item-icon"></span>
                                     <span>版本更新</span>
                               </div>
                               <div class="item-r">
                                   <span class="iconfont icon-fangxiang"></span>
                               </div>
                          </router-link>
                       </li>-->
                 </ul>

                 <ul class="me-list" style="margin-top:30px">
                 
                       <li>
                          <a  href="javascript:;" style="
    justify-content: center;text-align:'center'" @click="this.$root.logout">
                            
                             <div class="item-l" >
                                    退出登录
                               </div>
                            
                          </a>
                       </li>
                 </ul>
         </main>
  </div>
</template>

<script>
import NavBar from '../../common/NavBar/NavBar.vue'
export default {
  name: 'my',
  data () {
    return {
     username:null
    }
  },
  
  mounted(){
     let   user=this.$root.isLogin();
    //  alert(user.loginName);
 
    if(user||user.loginName){
      this.username=user.loginName
    }
  },
  
  components:{
      NavBar
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../../../assets/style/base.scss";
.me-list{
  >li{
      background:#fff;
      padding:rem(30px) rem(20px);
      margin:rem(20px) 0;
    
    >a{
    display:flex;
    justify-content: space-between;
    align-items:center;
    
    .item-l{
      font-size:18px;
       display:flex;
      .iconfont{
            font-size:rem(45px);
            color:$mainColor;
      }
     align-items:center;
     span{
   
        margin-left:rem(20px) 
     }
    }
    
    .icon-fangxiang{
      color:#cacaca;
    }
  }
   &.me-list-first{
      padding-top:rem(20px);
     padding-bottom:rem(20px);
     .item-l{
     
     span{
       margin-left:rem(40px) 
     }
    }
  .item-icon{
  
    height:rem(110px);
    height:rem(110px);
      width:rem(110px);
    }

   }
  }
  
}
</style>
