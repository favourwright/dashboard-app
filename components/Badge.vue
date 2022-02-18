<template>
<div :class="{'badge':true,'churned':churned}"><slot></slot></div>
</template>

<script>
export default {
  props:{
    churned:{default:false,Boolean}
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/sass/resources";
.badge{
  @include px(8px);
  @include py(4px);
  border-radius:50px;
  background:$green_faded;
  color:$green_dark;
  font-size:12px;
  font-weight:500;
  &.churned{
    color:$black;
    background:$grey_light_3;
  }
}
</style>
