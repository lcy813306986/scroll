<template>
  <div>
    <h2>公告栏文字停顿滚动</h2>
    <div class="textBox" @mouseenter="stop" @mouseleave="start">
      <div id="box" :key="1" ref="box">
        <ul v-for="(item,index) in dataList" :key="index"  @mouseenter="showInfo(index)" @mouseleave="hideInfo(index)">
        <text-tooltip
          :content="item.name"
          class="wid190"
          refName="supplierName"
        >
          <li>
            {{item.name}}
          </li>
        </text-tooltip>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import TextTooltip from './toolTip.vue'
export default {
  name: 'scroll',
   components: {
    TextTooltip
  },
  data () {
    return {
      textArr: [
        '1 第一条公告',
        '2 第二条公告第二条公告',
        '3 第三条公告第三条公告第三条公告',
        '4 第四条公告第三条公告第三条公告'
      ],
      list:[],
      dataList:[{
        name:'1',
        age:1
      },{
        name:'2',
        age:2
      },{
         name:'3',
        age:3
      }
      ,{
         name:'4',
        age:4
      },{
         name:'5',
        age:5
      },{
         name:'6',
        age:6
      },{
         name:'7',
        age:7
      },{
         name:'8',
        age:8
      },{
         name:'9',
        age:9
      },
      {
         name:'10',
        age:10
      },{
        name:'11',
        age:11
      },{
        name:'12',
        age:12
      },{
         name:'13',
        age:25
      }
      ,{
         name:'14',
        age:14
      },{
         name:'15',
        age:25
      },{
         name:'16',
        age:16
      },{
         name:'17',
        age:17
      },{
         name:'18',
        age:18
      },{
         name:'19',
        age:19
      },
      {
         name:'20',
        age:20
      }],
      number: 0,
      timer:'',
      show:false,
      current:""
    }
  },
  computed: {
    text () {
      return {
        id: this.number,
        val: this.textArr[this.number]
      }
    }
  },
  mounted () {
    this.startMove()
  },
  methods: {
    startMove () {
      this.dataList.push(this.dataList[this.number]);
      this.timer = setTimeout(() => {
        // if (this.number === 14) {
        //   this.number = 0;
        // } else {
        //   this.number += 1;
        // }
        this.number += 1;
        let top = -this.number*50;
        this.$refs['box'].style.transform = "translateY("+top+"px)"
        // this.dataList.shift();
        // this.list = this.dataList
        this.startMove();
      }, 2000); // 滚动不需要停顿则将2000改成动画持续时间
    },
    stop(e){
      clearTimeout(this.timer)
      console.log(e);
    },
    start(){
      let top = - this.number*50;
      this.$refs['box'].style.transform = "translateY("+top+"px)"
      this.startMove();
    },
    showInfo(index){
      this.show = true;
      this.current = index;
    },
    hideInfo(){
      this.show = false;
      this.current = '';
    }
  },
  destroyed() {
    clearTimeout(this.timer)
  },
}
</script>

<style scoped>
  h2 {
    padding: 20px 0
  }
  .textBox {
    width: 50%;
    height: 600px;
    margin: 0 auto;
    position: relative;
    text-align: center;
    overflow:hidden;
    border:1px solid #ccc;
  }
  #box{
    transition: all 0.5s linear;
  }
  #box ul{
    width:100%;
    height:50px;
    border-bottom:1px solid red;
    line-height:50px;
    margin:0px;
    position:relative;
  }
  .itemInfo{
    position:absolute;
    top:55px;
    left:0;
    right:0;
    margin:0 auto;
    width:60px;
    height:50px;
    background:black;
  }
  .text {
    width: 100%;
  }
</style>