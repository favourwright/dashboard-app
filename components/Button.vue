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
  padding:10px 16px;
  font-weight:500;
  font-size:14;
  border-radius:8px;
  background:unset;
  transition:.3s;
  &:hover{background: $grey_light;}
}
button.primary{background:$primary;}
button.border{
  border:1px solid #D0D5DD;
}
</style>
