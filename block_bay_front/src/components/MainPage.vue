<template>
  <div class="mainBody">

    <div class="leftBar">
      <LeftNavBar/>
    </div>
    <!--        数据可视化部分-->
    <div class="dataView">
        <router-view/>
      <!--        右侧个人中心组件-->
      <transition
          name="animate__animated animate__bounce"
          enter-active-class="animate__bounceInRight"
          leave-active-class="animate__fadeOutRight"
          appear
      >

      </transition>

    </div>

  </div>
</template>
<script>
import LeftNavBar from "@/components/Auxiliary/LeftNavBar";
import 'animate.css'
export default {
  name: "ManaGe",
  components:{LeftNavBar},
  data(){
    return{
      personalViewFlag:true
    }
  },
  mounted() {
    this.$bus.$on('personalCenterChange',(data)=>{
      this.personalViewFlag=data
    })
  }
}
</script>

<style scoped>
.mainBody{
  height: 100vh;
  background-color: #257B5E;
  display: flex;
  justify-content: center;
  align-items: center;
  display: flex;
  background-image: url("../assets/images/background.png");
  background-size: 100%;
  position: relative;
}
.dataView{
  width: 900px;
  height: 650px;
  background-color:#FDFFFD ;
  border-bottom-right-radius: 15px;
  border-top-right-radius: 15px;
  overflow: hidden;
  position: relative;
}
.personalCenter{
  position: absolute;
  right: 0px;
  top: 0px;
}
</style>