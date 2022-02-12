<template>
  <div class="avatar">
    <img :src="require(`~/assets/image/${img}`)" alt="avatar">
  </div>
</template>

<script>
export default {
  props:['img'],
}
</script>

<style lang="scss" scoped>
@import "../assets/sass/resources";
.avatar{
  @include flex;
  min-height:40px;
  min-width:40px;
  max-height:40px;
  max-width:40px;
  background:$grey;
  border-radius:50px;
  overflow:hidden;
  cursor:pointer;

  img{width:40px;}
}
</style>
