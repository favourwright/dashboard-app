<template>
  <div class="search">
    <div class="icon"><icon-search class="grey" /></div>
    <input :placeholder="name?name:'Search'" type="search" name="" id="">
  </div>
</template>

<script>
import IconSearch from "~icons/feather/search";
export default {
  props:['name'],
  components:{IconSearch}
}
</script>

<style lang="scss" scoped>
@import '../assets/sass/resources';
.search{
  width:320px;
  height:44px;
  border-radius:8px;
  border:1px solid $grey_light_2;
  overflow:hidden;
  position:relative;
  @include box-shadow;

  .icon{
    @include flex;
    height:100%;
    position:absolute;
    padding:0 12px;
  }

  input{
    height:100%;
    width:100%;
    border:none;
    border-radius:7px;
    padding:0 10px 0 40px;
    font-weight:400;
    font-size:16px;
  }
}
</style>
