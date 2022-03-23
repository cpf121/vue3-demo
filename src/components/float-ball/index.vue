<template>
  <div class="float-ball" :style="{bottom:bottom+'px',right:right+'px'}">
    <div class="content">
      <transition name="van-slide-up">
        <div class="operate-icons" v-if="showoperate">
          <div v-for="(item,idx) in operates" :key="idx" class="icon-item" @click="handleClick(item.operateName)">
            <van-icon :name="item.name" :size="item.size"></van-icon>
            <span v-if="item.content">{{item.content}}</span>
          </div>
        </div>
      </transition>
    </div>
    <van-icon name="plus" class="circle" :size="20" :class="showoperate?'roate':'roateback'" @click="showoperate=!showoperate"></van-icon>
  </div>
</template>
<script>
import {ref} from 'vue'
const showoperate=ref(false)
export default {
  props:{
    operates:{
      type:Array,
      default:()=>[]
    },
    bottom:{
      type:Number,
      default:100
    },
    right:{
      type:Number,
      default:20
    }
  },
  setup(prop,context){
    function handleClick(operateName){
      showoperate.value=!showoperate.value
      context.emit(operateName)
    }
    return {
      showoperate,
      handleClick
    }
  }
}
</script>
<style lang="scss" scoped>
.float-ball{
  position: fixed;
  z-index: 50;
  .content{
    position: relative;
    overflow: hidden;
    bottom: -20px;
    .operate-icons{
      width: 40px;
      border-radius: 40px 40px 0 0;
      background-color: #FFF;
      box-shadow: 0 0 5px #AAA;
      margin: 5px 5px 0 5px;
      padding-top: 10px;
      padding-bottom: 20px;
      text-align: center;
      .icon-item{
        font-size: 12px;
        width: 40px;
        margin: 5px 0;
        cursor: pointer;
        i{
          display: block;
        }
      }
    }
  }
  .circle{
    height: 40px;
    width: 40px;
    line-height: 40px;
    border-radius: 40px;
    text-align: center;
    color: white;
    background-color: #2365E0;
    margin: 5px 5px 0 5px;
    box-shadow: 0 0 5px #AAA;
  }
  .roate{
    animation:roate-fourtyfive .3s linear both;
  }
  .roateback{
    animation:roate-back .3s linear both;
  }
  @keyframes roate-fourtyfive {
    from{
      transform: rotate(0deg);
    }
    to{
      transform: rotate(45deg);
    }
  }
  @keyframes roate-back {
    from{
      transform: rotate(45deg);
    }
    to{
      transform: rotate(0deg);
    }
  }
}
</style>