<template>
<div class="filters">
  <main>
    <Button css='rtl bg_primary_faded' name="All time">
      <template #icon><icon-x class="ico" /></template>
    </Button>
    <Button css='rtl bg_primary_faded' name="US, AU, +4">
      <template #icon><icon-x class="ico" /></template>
    </Button>
    <Button name="More filters">
      <template #icon><img src="/filter-lines.svg"></template>
    </Button>
  </main>
  <Search />
</div>
</template>

<script>
import IconX from "~icons/feather/x";
export default {
  components:{
    IconX,
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/sass/resources';
.filters{
  display:flex;
  flex-direction:row;
  justify-content:space-between;
  margin-bottom:24px;
  @include pad_lr;
  main{
    display:flex;
    button:not(:last-child){
      margin-right:12px;
    }
  }
  @mixin mobile{
    flex-direction:column-reverse;
    gap:12px;
    main{
      button:nth-child(1){
        display:none;
      }
      button:nth-child(2){
        display:none;
      }
      button:nth-child(3){
        width:100%;
        justify-content:center;
      }
    }
    .search{
      width:100%;
    }
  }
  @include sm{@include mobile;}
  @include md{@include mobile;}

}

</style>
