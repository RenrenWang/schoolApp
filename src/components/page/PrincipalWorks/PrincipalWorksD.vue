<template>
  <div class="noticeD">
         <NavBar leftIcon="icon-fanhui"   fixed="true" title="本金工程详情"   @leftActive="back()"/>
         <main class="main">
                 <div class="top-noticeD" v-for="(v,index) in  details" :key="index">
                    
                                <p><span>支用编号：{{v.detailUsefundCod}}</span></p>
                                <p><span>使用项目：{{v.fundUseName}}</span></p>
                                <p><span>房屋：{{v.roomInfo}}</span></p>
                                <p><span>使用金额：{{v.useFund}}</span></p>
                                <p><span>使用日期：{{v.useDate}}</span></p>
                           
                     </div>
                         <!-- <h3>{{details.infoTitle}}</h3>
                          <div class="topN-info"> 
                                <p><span class=" iconfont  icon-shijian"></span><span>{{details.createDate}}</span></p>
                                <p><span class=" iconfont icon-chakan"></span><span>1000</span></p>
                           </div>  
                         
                 </div>
                  <div class="d-title">
					   	   <span class="line"></span>  
					   	      <h5>通知内容</h5>
					   	   <span class="line"></span>
				  </div>
                   <p class="notice-text">{{details.infoDescription}}</p> -->
         </main>
  </div>
</template>

<script>
import NavBar from '../../common/NavBar/NavBar.vue'

export default {
  name: 'noticeD',
  data () {
    return {
       details:[]
    }
  },

  mounted(){
      this.$http.get(BASEURL+'/fundInfoAction.action?myUseProjectInfo=&dataType=DET&pinfoId=32&fundUseId='+this.$route.params.id)
          .then((data)=>{
              data=data.data;
            this.details=data.data;
             console.log(JSON.stringify(this.details));
              
          })
    },
  methods:{
       back(){

      this.$router.go(-1);
     
   }
  },
  components:{
      NavBar,
     
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../../../assets/style/base.scss";
 .top-noticeD{
     display:flex;
       flex-direction:column;
       padding:rem(20px) rem(20px);
       >h3{
           font-size:18px;
           
       }
       p{
           margin-bottom: 10px;
           font-size:16px;
         margin-top:rem(10px);
       }
       .topN-info,.from{
         font-size:14px;
        color:$hColor;   
         margin-top:rem(30px);      
       }
       .topN-info{
          
           display:flex;
           flex-direction:row;
           justify-content: space-between;
        
       }
   
 }
     .d-title{
     	display: flex;
     	display: -webkit-flex;
     	height: rem(60px);
     	align-items: center;
     	 -webkit-align-items: center;
     }
    .d-title .line{
       border-bottom: 1px  dashed  #8f8f94;
     	height: 1px;
     	flex: 1;
     	-webkit-flex: 1;
     	
     }
    .d-title h5{
    	color: #8f8f94;
    	margin: 0 10px;
    	font-size: 16px;
    	
      }
      .notice-text{
        padding:rem(10px) rem(20px);
        font-size:16px;
        line-height:25px;
      }
</style>
