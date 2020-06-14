<template>
  <div class="friendLinks" ref="showbox">
    <div class="linkContent" ref="box" id="wrapper">
      <p id="demo1">nishi shenm</p>
      <p id="demo2">woshi shen</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
    }
  },
  created(){
    
  },
  mounted(){
      this.play();
  },
  methods: {
    play () {
        var speed = 100;
        var wrapper = document.getElementById('wrapper');
        var demo1 = document.getElementById('demo1');
        var demo2 = document.getElementById('demo2');
        demo2.innerHTML=demo1.innerHTML  
        console.log(demo2.innerHTML)
        function Marquee(){  
            if(demo2.offsetHeight-wrapper.scrollTop<=0)  
                wrapper.scrollTop-=demo1.offsetHeight;     
            else{  
                wrapper.scrollTop+=1 
            }  
        }  
        var MyMar=setInterval(Marquee,speed)  
        wrapper.onmouseover=function() {clearInterval(MyMar)}  
        wrapper.onmouseout=function() {MyMar=setInterval(Marquee,speed)} 
}, 
  }
}
</script>

<style scoped>
.linkContent {
  width: 90%;
  height: 20px;
  animation: move 3s infinite 2s running; 
  animation-fill-mode: forwards; 
}
@keyframes move {
    0% {
    transform:translatey(0px);
    }
    100% {
        transform:translateY(-20px);
    }
}
</style>