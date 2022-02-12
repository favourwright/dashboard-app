<template>
  <ul>
    <li
      v-for="(item, i) in items"
      :key="i" v-text="item.name"
      :class="{'active':item.isactive}">
    </li>
  </ul>
</template>

<script>
export default {
  props: ["items"],
};
</script>

<style lang="scss" scoped>
@import '../assets/sass/resources';
ul {
  display: flex;
  li {
    font-size: 16px;
    list-style: none;
    padding: 8px 12px;
    text-transform: capitalize;
    font-weight: 500;
    border-radius:6px;
    cursor:pointer;
    transition:.3s;

    &:hover{background: $grey_light;}
    &.active{background: $grey_light;}
  }
}
</style>
