<template>
  <div class=""  style="height:100%">
  
    <NavBar     leftIcon="icon-fanhui"   fixed="true" title="我的房产" @leftActive="back()"  />
    <main class="main"  style="height:100%;background:#f0eff4">
       <ul class="accountInfo-list">
          <li  v-for="(v,index) in houseList " key="index">
              <img :src="changeImgUrl(v.roomImguri)"/>
              <div class="ai-content">
                    <p>编号：{{v.personFundCod}}</p>
                    <p>房屋：{{v.houseNo}}幢{{v.unitId}}单元{{v.mainRoomId}}室</p>
                    <p><span>户主：朱向阳</span><span>身份证：123456</span></p>
                    <p>面积：{{v.mainArea}}㎡</p>
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
       houseList:[]
    }
  },
    mounted(){
      this.$http.get(BASEURL+'/homeInfo.action?homeType=CONMYS&pinfoId=32')
          .then((data)=>{
              data=data.data;
            this.houseList=data.data;
              
          })
    },
   methods:{
     changeImgUrl(imgUrl){
    return BASEURL+'/'+imgUrl;
     },
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
   
    align-items:center;
    >img{
      height:rem(180px);
      width:rem(180px);
    }
    >.ai-content{
      margin-left:10px;
    }
      p{
        font-size:14px;
        padding:2px 0;
         color: #929397;
        span:nth-type-of(2){
          margin-left:0 3px;
         
        }
      }
  }
}
</style>