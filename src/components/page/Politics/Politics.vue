<template>
  <div class="politics">
    <!-- rightIcon="icon-tianjia1"  -->
     <NavBar leftIcon="icon-fanhui"  fixed="true" title="政策法规" @leftActive="back()"  @rightActive="toUrl()"/>
     <main class="main">
<<<<<<< .mine
     <ul class="tab-bar">
            <li @click="tabSelect(Tab_1)">
                <a href="javascript:;":class="Tab_1==isTab?'active':''">部委</a>
||||||| .r4444
     <ul class="tab-bar">
            <li @click="tabSelect(Tab_1)">
                <a href="javascript:;":class="Tab_1==isTab?'active':''">本校</a>
=======
       <ul class="tab-bar">
            <li v-for="(v,index) in tabs" @click="clickBtn(index)">
                <a href="javascript:;" :class="{active:v.isActive}">{{v.name}}</a>
>>>>>>> .r4524
             </li>
<<<<<<< .mine
            <li  @click="tabSelect(Tab_2)">
               <a href="javascript:;" :class="Tab_2==isTab?'active':''">本省</a>
            </li>
             <li  @click="tabSelect(Tab_3)">
               <a href="javascript:;" :class="Tab_3==isTab?'active':''">其他省</a>
            </li>
     </ul>
        
    
     <div class="tab-bar-content" v-show="Tab_1==isTab">
      <p v-show="isLoading">正在加载...</p>
          <div class="listview listview-3">
                <LisViewItem_1  v-for="(v,i) in listviewdata_1" :listViewData="v" :key="i"/>
          </div>
     </div>
       <div class="tab-bar-content" v-show="Tab_2==isTab">
         <p v-show="isLoading">正在加载...</p>
          <div class="listview listview-3">
               <LisViewItem_1  v-for="(v,i) in listviewdata_2" :listViewData="v" :key="i"/>
          </div>
     </div>
       <div class="tab-bar-content" v-show="Tab_3==isTab">
         <p v-show="isLoading">正在加载...</p>
          <div class="listview listview-3">
               <LisViewItem_1  v-for="(v,i) in listviewdata_3" :listViewData="v" :key="i"/>
          </div>
       </div>
   
||||||| .r4444
            <li  @click="tabSelect(Tab_2)">
               <a href="javascript:;" :class="Tab_2==isTab?'active':''">本省</a>
            </li>
             <li  @click="tabSelect(Tab_3)">
               <a href="javascript:;" :class="Tab_3==isTab?'active':''">行业</a>
            </li>
     </ul>
        
    
     <div class="tab-bar-content" v-show="Tab_1==isTab">
      <p v-show="isLoading">正在加载...</p>
          <div class="listview listview-3">
                <LisViewItem_1  v-for="(v,i) in listviewdata_1" :listViewData="v" :key="i"/>
          </div>
     </div>
       <div class="tab-bar-content" v-show="Tab_2==isTab">
         <p v-show="isLoading">正在加载...</p>
          <div class="listview listview-3">
               <LisViewItem_1  v-for="(v,i) in listviewdata_2" :listViewData="v" :key="i"/>
          </div>
     </div>
       <div class="tab-bar-content" v-show="Tab_3==isTab">
         <p v-show="isLoading">正在加载...</p>
          <div class="listview listview-3">
               <LisViewItem_1  v-for="(v,i) in listviewdata_3" :listViewData="v" :key="i"/>
          </div>
       </div>
   
=======
           
        </ul>
         <!-- let u=this.$http.get(BASEURL+'/newsAction.action?affType=R&policyType=U&pageno=1');
        let r=this.$http.get(BASEURL+'/newsAction.action?affType=R&policyType=R&pageno=1');
        let m=this.$http.get(BASEURL+'/newsAction.action?affType=R&policyType=M&pageno=1');   -->
		    <div class="tab-content">
              <ListView v-show="tabs[0].isActive" warpId="datalist1" mId="mescroll1" url="/newsAction.action?affType=R&policyType=U&pageno="/>
              <ListView  v-show="tabs[1].isActive" warpId="datalist2" mId="mescroll2" url="/newsAction.action?affType=R&policyType=R&pageno="/>
               <ListView v-show="tabs[2].isActive" warpId="datalist3" mId="mescroll3" url="/newsAction.action?affType=R&policyType=M&pageno="/>
		    </div>
>>>>>>> .r4524
     </main>
  </div>
</template>
  
<script>
import NavBar from '../../common/NavBar/NavBar.vue'
import LisViewItem_1 from '../../common/LisViewItem/LisViewItem_1.vue'
import ListView from '../../common/ListView'
export default {
  name: 'notice',
  data () {
    return {
      tabs:[
        {name:'本校',isActive:true},
        {name:'本省',isActive:false},
        {name:'行业',isActive:false}
      ]
      }
    },

 mounted(){
  
  },
  methods:{
     clickBtn(index){
        this.tabs.map((item,index)=>{
          item.isActive=false;
        })
       this.tabs[index].isActive=true;
     },
       back(){

      this.$router.go(-1);
     
   },
   toUrl(){
     this.$router.push({ path: '/addNotice' });
   }
   },
      

  components:{
    NavBar,
   ListView
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
@import "../../../assets/style/base.scss";
.tab-content{
  position: fixed;
  top:$topBarH+rem(100px);
  bottom:0;
  overflow-y: auto;
 width: 100%;
}
.notice{
   .tab-bar-content{
     background:$mianBgColor;
      overflow:hidden;
   }
}
.tab-content{
  position: fixed;
  top:$topBarH+rem(100px);
  bottom:0;
  overflow-y: auto;
 
}
.tab-bar{
  position: relative;
  z-index: 9999;
     display:flex;
    
     text-align:center;
     align-items:center;
     height:rem(100px);
     line-height:rem(100px);
    overflow:hidden;
   background: #fff;
  
     >li{
       position:relative;
       flex:1;
     
         box-sizing: border-box;
      //   &:after{
      //       @extend %borderBottomLine;
      // }
      border-bottom:5px solid $borderColor;
      &:before{
            @extend %borderRightLine;
      }
       >a{
         
         font-size:16px;
         &.active{
           color:$mainColor;
  
         }
       }
     }
}

</style>
