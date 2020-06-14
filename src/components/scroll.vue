<template>
  <div id="box">
    <ul id="con1" ref="con1" :class="{anim:animate==true}"  @mouseenter="starTime" @mouseleave="clear">
      <li v-for='(item,index) in items' :key="index" @mouseenter="stop(index)" @mouseleave="start(index)">
        {{item.name + item.name}}
        <div v-if="show && index==current">dsvdasd</div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      animate:false,
      items:[  //消息列表对应的数组
        {name:"马云"},
        {name:"雷军"},
        {name:"王勤"},
        {name:"马云1"},
        {name:"雷军1"},
        {name:"王勤1"},
        {name:"马云2"},
        {name:"雷军2"},
        {name:"王勤2"},
      ],
      page: [1, 2, 3, 4, 5],
      interval:null,
      setTime:null,
      show:false,
      current:""
    }
  },
  created(){
    this.interval = setInterval(this.scroll,2500)
  },
  methods: {
    scroll(){
      this.animate = true
      this.setTime = setTimeout(() => {
        this.items.push(this.items[0]);
        this.items.shift();
        this.animate= false;  // 这个地方如果不把animate 取反会出现消息回滚的现象，此时把ul 元素的过渡属性取消掉就可以完美实现无缝滚动的效果了
      },1000)
    },
    stop(index){
      this.show = true;
      this.current = index;
    },
    start(){
      this.show = false;
      this.current = '';
    },
    starTime(){
      clearInterval(this.interval);
      this.setTime=null
    },
    clear(){
      this.scroll()
      this.interval = setInterval(this.scroll,2500)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  *{
    margin: 0 ;
    padding: 0;
  }
  #box{
    width: 300px;
    height: 300px;
    line-height: 30px;
    overflow: hidden;
    padding-left: 30px;
    border: 1px solid black;
    transition: all 0.5s;
  }
  .anim{
    transition: all 1.5s;
    margin-top: -34px;
  }
  #con1 li{
    margin-top: 5px;
    list-style: none;
    line-height: 34px;
    height: 40px;
  }
</style>