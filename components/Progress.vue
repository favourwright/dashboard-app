<template>
<div class="progress-bar" :class="css">
  <div class="progress" :style="`width:${progress}%`"></div>
</div>
</template>

<script>
export default {
  props:{
    progress:{
      default:0,Number
    },
    css:String
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/sass/resources";
.progress-bar{
  position:relative;
  width:88px;
  height:8px;
  border-radius:50px;
  overflow:hidden;
  background:$primary_faded;
  .progress{
    position:absolute;
    left:0;
    top:0;
    height:100%;
    border-radius:50px;
    background:$primary;
    transition:.3s;
  }

}
</style>
