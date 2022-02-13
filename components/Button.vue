<template>
  <button class="border">
    <slot name="icon"></slot>
    {{name}}
  </button>
</template>

<script>
export default {
  props:['name'],
}
</script>

<style lang="scss" scoped>
@import '../assets/sass/resources';
button{
  display:flex;
  align-items:center;
  padding:10px 16px;
  font-weight:500;
  font-size:14px;
  border-radius:8px;
  background:unset;
  transition:.3s;
  @include box-shadow;
  @include unselectable;
  &:hover{background: $grey_light_1;}
}
button.primary{
  background:$primary;
  color:#fff;
}
button.border{
  border:1px solid $grey_light_2;
}
</style>
