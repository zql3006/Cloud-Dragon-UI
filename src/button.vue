<template>
  <button class="c-button" :class="{[`icon-${iconPosition}`]:true}" @click="$emit('click')">
    <c-icon class="icon" :name="icon" v-if="icon && !loading"></c-icon>
    <c-icon class="loading icon" name="loading" v-if="loading"></c-icon>
    <div class="content">
      <slot></slot>
    </div>
  </button>
</template>
<script>
import Icon from './icon'
export default {
  components:{
    "c-icon":Icon,
  },
  props:{
    icon:{},
    loading:{
      type:Boolean,
      default:false
    },
    iconPosition:{
      type:String,
      default:'left',
      validator(value){
        return value !== 'left' || value !== 'right'
      }
    }
  }
}
</script>
<style lang="scss">
  @keyframes spin {
    0%{ transform: rotate(0deg); }
    100%{ transform: rotate(360deg); }
  }
  .c-button{
    font-size: var(--font-size);
    height: var(--button-height);
    border-radius: var(--border-radius);
    border:1px solid var(--border-color);
    background: var(--button-bg);
    padding: 0 1em;
    display: inline-flex;
    justify-content: center;
    align-items: center;
    vertical-align: middle;
    &:hover{
      border-color: var(--border-color-hover);
    }
    &:active{
      background-color: var(--button-active-bg);
    }
    &:focus{
      outline: none;
    }
    >.icon{
      order:1;
      margin-right: .1em;
    }
    >.content{
      line-height: 1em;
      order:2;
    }
    &.icon-right{
      >.icon{
        order:2;
        margin-right: 0;
        margin-left: .1em;
      }
      >.content{
        order:1;
      }
    }
    .loading{
      animation: spin 1s linear infinite;
    }
  }
</style>