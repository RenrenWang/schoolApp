<template>
  <div class=""  style="height:100%">
  
    <NavBar     leftIcon="icon-fanhui"   fixed="true" title="服务指南" @leftActive="back()"  />
    <main class="main"  style="height:100%;background:#f0eff4">
       <ul class="accountInfo-list">
        
         <router-link  v-for="(v,index) in newsList " :key="index" :to="{ name: 'serviceGuideD', params: { id: v.infoId }}" tag="li">      
              <div class="ai-content">
                    <h3>{{v.infoTitle}}</h3>
                  
               <p><span>{{v.createDate}}</span><span><span class=" iconfont icon-chakan"></span>{{v.attachCount}}</span></p>
                 
              </div>
          </router-link>
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
      this.$http.get(BASEURL+'/newsAction.action?newsType=SR&pageno=1')
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