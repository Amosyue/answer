<template>
  <div class="score">
    <v-header></v-header>
  </br> </br> </br> </br> </br> </br>
    <div class="tac">
      <h1>得分</h1>
      <div class="btn">{{score}}</div>
      <p>下边是测试数据，可以忽略</p>
      {{scoreTips}}{{itemNum}}{{answerid}}
    </div>
    <v-footer></v-footer>
  </div>
</template>

<script>
import vheader from '../../components/common/header.vue';
import vfooter from '../../components/common/footer.vue';

import { mapState, mapActions } from 'vuex'
export default {
  name: 'score',
  data () {
    return {
      showHide: false, //是否显示提示
      score: 0, //分数
      scoreTips:'', //分数提示
      rightAnswer: [2, 7, 12, 13, 18], //正确答案
      scoreTipsArr:['你说，是不是把知识都还给小学老师了？','还不错，但还需要继续加油哦！','不要嘚瑟还有进步的空间！','智商离爆表只差一步了！','你也太聪明啦！']
    }
  },
  created:function(){
     this.getScore()
  },
  computed:{
    ...mapState([
        'answerid',
        'itemNum'
    ])
  },
  methods:{
    ...mapActions([
        'reset'
    ]),
      getScore:function(){
        this.itemNum=1
         this.answerid.forEach((item,index)=>{
            if(item==this.rightAnswer[index]){
                 this.score+=20;
            }
         })
         if(this.score<=20){
            this.scoreTips=this.scoreTipsArr[0]
         }else if(this.score<=40){
            this.scoreTips=this.scoreTipsArr[1]
         }else if(this.score<=60){
            this.scoreTips=this.scoreTipsArr[2]
         }else if(this.score<=80){
            this.scoreTips=this.scoreTipsArr[3]
         }else if(this.score<=100){
            this.scoreTips=this.scoreTipsArr[4]
         }
         //为了重置vuex里面的数据，不然返回时候报错
         this.reset()
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

