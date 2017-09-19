<template>
  <div class="">
  
    <NavBar     leftIcon="icon-fanhui"   fixed="true" title="账户信息" @leftActive="back()"  />
    <main class="main">
       <ul class="">
          <li class="accountInfo-list">
              <div class="ai-content">
                    <p>编号：120154425</p>
                    <p>户主：朱向阳</p>
              </div>
          </li>
       </ul>
    </main>
  </div>
</template>

<script>
import NavBar from '../../common/NavBar/NavBar.vue'
export default {
  name: '',
  data () {
    return {
   
    }
  },
   methods:{
       back(){

       this.$router.go(-1);
     
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
</style>