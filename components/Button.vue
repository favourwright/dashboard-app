<template>
  <button :class="{
    [css]: css && css.trim(' ')!='rtl',
    'border rtl':css.trim(' ')=='rtl',
    'has-icon':hasIcon,
    }">
    <slot name="icon"></slot>
    {{name}}
  </button>
</template>

<script>
export default {
  props:{
    name :{ default: 'Button', String },
    css :{ default: 'border', String }
  },
  computed: {
    hasIcon () {
      return !!this.$slots['icon']
    }
  }
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
  border:none;
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
button.has-icon{
  svg.ico, img{
    margin-right:8px;
  }
  &.rtl{
    flex-direction: row-reverse;
    svg, img{
      margin-right:0;
      margin-left:8px;
    }
  }
}
</style>
