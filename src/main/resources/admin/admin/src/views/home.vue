<template>
<div class="content">

<div class="text main-text">你好,这里是{{this.$project.projectName}}</div>
<div class="title-container"><h1 class="title" style="color: rgb(0,218,164)">FIND YOUR OWN NEED.</h1></div>

</div>
</template>
<script>
import router from '@/router/router-static'
export default {
  mounted(){
    this.init();
  },
  methods:{
    init(){
        if(this.$storage.get('Token')){
        this.$http({
            url: `${this.$storage.get('sessionTable')}/session`,
            method: "get"
        }).then(({ data }) => {
            if (data && data.code != 0) {
            router.push({ name: 'login' })
            }
        });
        }else{
            router.push({ name: 'login' })
        }
    }
  }
};
</script>

<style lang="scss" scoped>
.content {
  display: flex;
  align-items: center;
  flex-direction: column;
  width: 100%;
  height: 100%;
  min-height: 500px;
  text-align: center;
  background-image: url('http://localhost:8080/wangshangshangchengB/upload/market.jpg'); /* 设置背景图片的路径 */
  background-size: cover; /* 确保背景图片覆盖整个容器 */
  background-position: center; /* 让背景图片居中 */
  .main-text{
    font-size: 38px;
    font-weight: bold;
    margin-top: 15%;
    color: #bc3f3f;
  }
  .text {
    font-size: 38px;
    font-weight: bold;
    color: #02fbd6;
  }
}
</style>