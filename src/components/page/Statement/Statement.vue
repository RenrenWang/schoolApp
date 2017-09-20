<template>
  <div class=""  style="height:100%">
  
    <NavBar     leftIcon="icon-fanhui"   fixed="true" title="结存单" @leftActive="back()"  />
    <main class="main"  style="height:100%;background:#f0eff4">
       <ul class="accountInfo-list">
        
         <li v-for="(v,index) in newsList " :key="index" >      
              <div class="ai-content">
                  
                  
               <p><span>姓名：{{v.personName}}</span><span>身份证：{{v.personCardid}}</span></p>
               <p><span>结存时点：{{v.ordTime}}</span><span>期初金额：{{v.periodQc}}</span></p> 
               <p><span>入库金额：{{v.periodRk}}</span><span>使用金额：{{v.periodCk}}</span></p> 
                <p><span>利息金额：{{v.periodLx}}</span><span>账户余额：{{v.periodYe}}</span></p>
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
     newsList:[]
    }
  },
    mounted(){
      this.$http.get(BASEURL+'/fundInfoAction.action?myOrderInfo=&pinfoId=32')
          .then((data)=>{
              data=data.data;
            this.newsList=data.data;
              
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
    h3{
        font-size:16px;
    }
    .ai-content{
        width:100%;
    }
      p{
          width:100%;
      margin-top:10px;
        font-size:14px;
        padding:2px 0;
      display:flex;
        flex-direction:row;
     justify-content: space-between;
       
      }
  }
}
</style>