<template>
  <div class="about">
     <NavBar  leftIcon="icon-fanhui"  fixed="true" title="技术支持" @leftActive="back()"/>
         <main class="main">
         	<!--
               <div class="about-img">
                  <img src="../../../assets/images/about.jpg"/>
               </div>-->
              <br /><br />
               <p>
               	<div>
		               <div class="about-img" style="text-align: center;">
		                  <img src="../../../assets/images/vender_logo.png" style="width: 80px; height: 80px;"/>
		                  <p><span></span></p>
		                  <br />
		                  <p align="center"><font style="font-size:large ;">荣智信息科技</font></p>		                                    
		               </div>
		               <div style="text-align: center;">
		               	<p><span><font style="font-size:large ;">联系电话&nbsp;&nbsp;:&nbsp;&nbsp;13958065386</font></span></p>
		               	<br />
		               	<p><span><font style="font-size:large ;">QQ &nbsp;&nbsp;:&nbsp;&nbsp;664267685</font></span></p>
		               	<br />
		               	<p><span>&nbsp;&nbsp;<font style="font-size:large ;">二维码网址</font>&nbsp;&nbsp;</span></p>
		               	<br />
		               	<a href="http://www.hzrongzhi.cn/" target="_blank"><img src="../../../assets/images/ercode.jpg"/></a>
		               </div>  
               </div>
               </p>
         </main>
 
  </div>
</template>

<script>
import NavBar from '../../common/NavBar/NavBar.vue'
export default {
  name: 'about',
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
.about-img{
    height:rem(350px);
    img{
        width:100%;
        height:100%;
    }
}
.about-text{
    text-indent:20px;
    line-height:25px;
    text-align:left;
    font-size:14px;
    padding:rem(15px);
}
</style>
