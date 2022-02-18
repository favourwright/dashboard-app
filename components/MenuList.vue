<template>
  <ul :class="{'can-wrap':can_wrap}">
    <li
      v-for="(item, i) in items"
      :key="i" v-text="item.name"
      :class="{'active':item.isactive}">
    </li>
  </ul>
</template>

<script>
export default {
  props:{
    items:Array,
    can_wrap:{default:false,Boolean}
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/sass/resources';
ul {
  display: flex;
  &.can-wrap{
    flex-wrap:wrap;
    @include py(10px);
  }
  li {
    font-size: 16px;
    list-style: none;
    padding: 8px 12px;
    text-transform: capitalize;
    font-weight: 500;
    border-radius:6px;
    cursor:pointer;
    transition:.3s;
    &:hover{background: $grey_light_1;}
    &.active{background: $grey_light_1;}
  }
}
</style>
