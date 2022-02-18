<template>
<div class="avatar-group">
  <template v-for="(n,i) in users">
    <div :key="i" class="each" v-show="!(i==users.length-1 && n=='')" :class="`t-${i}`">
      <img v-if="i!=users.length-1" :src="require(`~/assets/image/${n}`)" alt="avatar">
      <div v-else>+{{n}}</div>
    </div>
  </template>
</div>
</template>

<script>
export default {
  props:{
    users:Array
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/sass/resources";
.avatar-group{
  @include flex(flex-start);
  .each{
    @include flex;
    height:24px;
    width:24px;
    background:$primary_faded;
    border-radius:50px;
    border:1.5px solid #fff;
    overflow:hidden;
    box-sizing: content-box;
    &:last-child{
      border-width:2px;
    }
    * {
      font-size:12px;
      font-weight:500;
      color:$primary;
    }
    img{
      width:100%;
    }
    $space: (1,2,3,4,5,6);
    $factor:6;
    @each $each in $space {
        &.t-#{$each} {
          transform: translateX(-#{ ($each * $factor) }px);
        }
    }
  }
}
</style>
