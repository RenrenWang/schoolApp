<template>
  <div class="share">
    <NavBar leftIcon="icon-fanhui"   fixed="true" title="分享" @leftActive="back()"  />
     <main class="main">     		 	
             
       	<div>
               <div class="about-img" style="text-align: center;">		                 
                  <br /> <br />
                  <p align="center"><font style="font-size:large ;"><b>房产APP安装方法</b></font></p>	
                   <br /> <br />
               </div>
            	
            <div>
            	 <a href="https://www.pgyer.com/Lz3p" target="_blank></a>"<img src="../../../assets/images/gisapp.png" style="width: 200px; height: 180px;"/></a>
  		 			<br />
  		 			</div>
  		 </div>
		                			   
           <div style="font-size: large;">
           	 <br />
           	<p style="text-decoration: underline;"><a href="https://www.pgyer.com/Lz3p" target="_blank">链接安装APP</a></p>
           	 <br />
           </div>
           <br /><br /><br />
           <div class="text">
             	<p>扫描上方二维码或</p>
             	<p>在浏览器打开链接。</p>
              <p>与朋友分享此APP客户端吧！</p>
           </div>
           
     </main>
 
  </div>
</template>

<script>
import NavBar from '../../common/NavBar/NavBar.vue'
export default {
  name: 'Share',
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
.main{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    .text{
      text-align: center;
      font-size: 16px;
      line-height: 30px;
    }
}
</style>
