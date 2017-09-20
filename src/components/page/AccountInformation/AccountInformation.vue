<template>
  <div class=""  style="height:100%">
  
    <NavBar     leftIcon="icon-fanhui"   fixed="true" title="账户信息" @leftActive="back()"  />
    <main class="main"  style="height:100%;background:#f0eff4">
      <ul  class="ai-tab-list">
         <li v-for="(v,index) in tabList" :class="{isSelect:v.isSelect}" :key="index" @click="selectTab(index)">{{v.name}}</li>
      </ul>
      <ul class="accountInfo-list">
        
         <li  v-for="(v,index) in newsList " :key="index" >      
              <div class="ai-content" v-if="detailType=='IN'">
                  
                  
                <p><span>缴存编号：{{v.detailInfundCod}}</span><span>房号：{{v.roomInfo}}</span></p>
                <p><span>金额：{{v.infund}}￥</span><span>日期：{{v.indate}}</span></p> 
                 <p><span>类型：{{v.infundType}}</span></p>   
              </div>
               <div class="ai-content" v-if="detailType=='USE'">
                  
                  
                <p><span>使用编号：{{v.detailUsefundCod}}</span><span>使用项目：{{v.fundUseName}}</span></p>
                <p><span>房号：{{v.roomInfo}}</span><span>金额：{{v.useFund}}￥</span></p> 
                 <p><span>日期：{{v.useDate}}</span></p>   
              </div>
              <div class="ai-content" v-if="detailType=='LX'">
                  
                  
            
                <p><span>房号：{{v.roomInfo}}</span><span>本金：{{v.bj}}￥</span></p> 
                 <p><span>利息时间点：{{v.lxDate}}</span><span>利息：{{v.lx}}</span></p> 
                   <p><span>累计利息：{{v.ljLx}}</span><span>利息合计：{{v.ljBj}}</span></p>    
              </div>
              <div class="ai-content" v-if="detailType==''">
                  
                  
            
                <p style="justify-content:center;align-items:center"><span>暂无数据</span></p> 
                 
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
     newsList:[],
     tabList:[
         {name:"流水",isSelect:true,detailType:"ZS"},
         {name:"缴存",isSelect:false,detailType:"IN"},
         {name:"使用",isSelect:false,detailType:"USE"},
         {name:"退款",isSelect:false,detailType:""},
         {name:"利息",isSelect:false,detailType:"LX"},
         {name:"增值",isSelect:false,detailType:""}
         ],
          detailType:'ZS'
    }
   
  },
    mounted(){
      this.getDtata();
    },
   methods:{
     changeImgUrl(imgUrl){
         return BASEURL+'/'+imgUrl;
     },
     back(){
       this.$router.go(-1);
     },

     getDtata(){
      this.$http.get(BASEURL+'/fundInfoAction.action?myDetailInfo=&detailType='+this.detailType+'&personFundId=1023')
          .then((data)=>{
           data=data.data;
           if(this.detailType=='ZS')
            this.newsList=data.inData;
            else
             this.newsList=data.data;  
          })
     },
     selectTab(number){
     
         this.tabList.map((item,index)=>{
              this.tabList[index]['isSelect']=false;
         })
        this.tabList[number]['isSelect']=true;

        if(this.tabList[number]['detailType']&&this.tabList[number]['detailType']!=""){
            this.detailType=this.tabList[number]['detailType'];
             this.getDtata();
        }else{
         this.detailType='';
         this.newsList=[0];
        }
       
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
.isSelect{
    color:$mainColor;
}
.ai-tab-list{
  display:flex;
    flex-direction:row;
    background:#fff;
    padding:15px 0;
    justify-content:center;
    align-items:center;
    >li{
        text-align:center;
        flex:1;
        font-size:14px;
    }
}
.accountInfo-list{
    margin-top:10px;
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