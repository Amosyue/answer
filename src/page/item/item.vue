<template>
  <div class="item">
    <div v-if="itemData.length > 0">
        <div>{{itemData[itemNum-1].topic_name}}</div>
        <ul>
          <li v-for="(liItem,index) in itemData[itemNum-1].topic_answer" @click="selectOption(index, liItem.topic_answer_id)">
            <p :class="{'cur':choosedNum==index}"><span>{{chooseType(index)}}、</span>{{liItem.answer_name}}</p>
          </li>
        </ul>
    </div> 
    <p style="color:blue;margin-top:15px;">下边是调试数据，可忽略</p>
    <p>第几题：{{itemNum}}</p>
    <p>答案集合：{{answerid}} </p>

    <div class="btn" @click="nextQuestion">
      <span v-if="itemNum<itemData.length">下一题</span>
      <span v-else>提交答案</span>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import Resource from 'vue-resource'
import { mapState, mapActions } from 'vuex'
Vue.use(Resource)

export default {
  name: 'item',
  data () {
    return {
      itemData:"",
      choosedNum:null,//选中的答案索引值
      choosedId:null//选中的答案id
    }
  },
  computed: mapState([
      'level', //活动周数
      'itemNum', // 第几题
      'answerid' //答案id集合
  ]),
  created: function() {
    this.getData();
  },
  methods: {
    ...mapActions([
        'addNum'
    ]),
    getData:function(){
        this.$http({
              url:'static/data.json',// 这个地方注意一下，本地json文件放在static文件里
              method:'GET'
            }).then(function(response){
            this.itemData=response.body.itemDetail;
        })
    },
    chooseType: type => { //格式化函数A,B,C,D
      switch(type){
        case 0: return 'A';
        case 1: return 'B';
        case 2: return 'C';
        case 3: return 'D';
      }
    },
    //选择答案
    selectOption:function(type,id){ 
      this.choosedNum=type;
      this.choosedId=id
    },
    //下一题以及提交答案
    nextQuestion:function(index){
       if(this.choosedNum !== null) {
          this.choosedNum = null;
          //保存答案, 题目索引加一，跳到下一题
          this.addNum(this.choosedId)
           // debugger
          if(this.itemNum>this.itemData.length){
            this.$router.push('score')
          }
        }else{
          alert('您还没有选择答案哦')
        }
    }
  }
}
</script>
<style lang="less">
  @import './item.less';
</style>
