<template>
  <div class=""  style="height:100%">
  
    <NavBar     leftIcon="icon-fanhui"   fixed="true" title="账户信息" @leftActive="back()"  />
    <main class="main"  style="height:100%;background:#f0eff4">
       <ul class="accountInfo-list">
          <li  v-for="v in 10 ">
              <div class="ai-content">
                    <p>编号：120154425</p>
                    <p>房屋：1幢2单元3号楼</p>
                    <p><span>户主：朱向阳</span><span>身份证：123456</span></p>
                    <p>面积：100M2</p>
                    <p>帐户余额：2500¥</p>

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
.accountInfo-list{
  >li{
    padding:6px 10px;
    background:#fff;
    border-bottom:1px solid  #f1f1f1;
      display:flex;
      flex-direction:row;
      justify-content:space-between;
      align-items:center;
      p{
        font-size:14px;
        padding:2px 0;
        span:nth-type-of(2){
          margin-left:0 3px;
        }
      }
  }
}
</style>