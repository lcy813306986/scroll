<template>
  <div class="text-tooltip">
    <el-tooltip popper-class="good" effect="dark" :disabled="isShowTooltip" :content="content" placement="bottom">
      <p class="over-flow" :class="className" >
        <span :ref="refName">{{content||'-'}}</span>
      </p>
    </el-tooltip>
  </div>
</template>

<script>
  export default {
    name: 'textTooltip',
    props: {
      // 显示的文字内容
      content: {
        type: String,
        default: () => {
          return ''
        }
      },
      // 外层框的样式，在传入的这个类名中设置文字显示的宽度
      className: {
        type: String,
        default: () => {
          return ''
        }
      },
      // 为页面文字标识（如在同一页面中调用多次组件，此参数不可重复）
      refName: {
        type: String,
        default: () => {
          return ''
        }
      }
    },
    data() {
      return {
        isShowTooltip: false
      }
    },
    methods: {
    }
  }
</script>

<style  lang="scss" scoped>
  
  .item{
    background: #cccccc !important;
    width: 100px !important;
  }
.over-flow {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
.wid190 {
	width: 100px;
}
</style>