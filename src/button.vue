<template>
  <button class="c-button">按钮</button>
</template>
<script>
export default {
  
}
</script>
<style lang="scss">
  .c-button{
    font-size: var(--font-size);
    height: var(--button-height);
    border-radius: var(--border-radius);
    border:1px solid var(--border-color);
    background: var(--button-bg);
    padding: 0 1em;
    &:hover{
      border-color: var(--border-color-hover);
    }
    &:active{
      background-color: var(--button-active-bg);
    }
    &:focus{
      outline: none;
    }
  }
</style>