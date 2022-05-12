<template>
  <div>
    <div class="title">刺猬水果店</div>
    <fruit-shop/>
  </div>
</template>

<script>
import FruitShop from "./page/FruitShop.vue";
export default {
  name: 'App',
  components: {
    FruitShop
  },
  data(){
    return{

    }
  }
}
</script>

<style lang="less" scoped>
.title {
  width: 100%;
  height: 50px;
  background-color: #FC4F59;
  color: whitesmoke;
  font-size: 20px;
  text-align: center;
  line-height: 50px;
  position: fixed;

}
</style>