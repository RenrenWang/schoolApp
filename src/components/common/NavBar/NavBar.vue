<template>

        <header :class="['navbar',fixed?'fixed':'']" >
       
            <div class="left" v-if="leftIcon">
                 <a href="javascright:;" class="navbar-item" @click="leftActive">
                     <span :class="['iconfont',leftIcon]"></span>
                 </a>
            </div>
            <input type="text"  v-show="isShowSelect?isShowSelect:false" placeholder="请输入搜索的楼幢" style="position:raltive;z-index:999;background:#fff;padding-left:5px;height:30px;border:none;width:70%;border-bottom:1px  solid #bbb;outline:none"/>
            <h1 class="center title" v-if="title">{{title}}</h1>
            <h1 class="center title  logobox" v-if="logo"><img :src="logo" class="logo"/>高校房产移动平台
</h1>
            <div class="right"  v-if="rightIcon">
              
                 <a  href="javascright:;" class="navbar-item" style="margin-right:15px" @click="rightActiveTwo" v-if="rightIconTwo?true:false">
                     <span :class="['iconfont',rightIconTwo]" ></span>
                 </a>
                 <a  href="javascright:;" class="navbar-item" @click="rightActive">
                     <span :class="['iconfont',rightIcon]"></span>
                 </a>
            </div>
       </header>
 
</template>

<script>


export default {
  name:'navbar',
  props:["title","fixed","logo","leftIcon","rightIcon","rightIconTwo","isShowSelect"],

  methods:{
     
    leftActive(){
    
       this.$emit('leftActive');
    },
     rightActive(){
     
       this.$emit('rightActive');
    },
    rightActiveTwo(){
        this.$emit('rightActiveTwo');
    }
 }
}
</script>

<style lang="scss" scoped>

@import "../../../assets/style/base.scss";
.logobox{
  display:flex;
  align-items:center;
  justify-content:center;
  flex:1;
}
.navbar{
  position:relative;
  height:$topBarH;
  background:$mainColor;
  box-shadow: 0 1px 3px rgba(0,0,0,.12), 0 1px 2px rgba(0,0,0,.24);
  display:flex; 
  justify-content:space-between;
  align-items:center;

  padding:0 rem(20px);
box-sizing:border-box;
 &.fixed{
   position:fixed;
   z-index:9999;
   width:100%;
 }

  .title,.iconfont,.nav-bar-text{
    color:#fff;
    
  }
  .nav-bar-text{
    font-size:16px;
    line-height:1;
  }
  .iconfont{
   
    font-size:rem(55px);
    transform:translateY(30px);
  }
  .logo{
    height:$topBarH - rem(20px);
  
  }
 .title {
   text-align:center;
    font-size:18px;
    
    
  }

  .center{
    position:absolute;
    width:100%;
    left:50%;
    top:50%;
    transform:translate3d(-50%,-50%,0);
    img{
      width:rem(80px);
      height:rem(80px);
      margin-right:5px;
    }
  }
}


</style>
