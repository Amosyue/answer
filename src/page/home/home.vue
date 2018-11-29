<template>
  <div class="home">
    <v-header></v-header>
    <div class="tac">
      <h1>智力测试1234</h1>
      <div class="btn"><router-link to="item">开始答题</router-link></div>
    </div>
    <v-footer></v-footer>
  </div>
</template>

<script>
import vheader from '../../components/common/header.vue';
import vfooter from '../../components/common/footer.vue';
export default {
  name: 'home',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  components: {
    'vHeader': vheader,
    'vFooter': vfooter
  }
}
</script>
<style scoped>
  .btn{
    border:1px solid blue;
    height:1rem;
    line-height: 1rem;
    display: block;
    width:4rem;
    margin:2rem auto;
  }
</style>

