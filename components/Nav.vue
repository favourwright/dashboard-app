<template>
  <nav>
    <div class="primary-nav">
      <div>
        <Logo />
        <MenuList :items="[
          { name:'home' },
          { name:'dashboard', isactive:true },
          { name:'projects' },
          { name:'tasks' },
          { name:'reporting' },
          { name:'users' },
        ]" />
      </div>
      <div>
        <Button name="Upgrade now">
          <template v-slot:icon><icon-zap style="font-size: 2em; color: red"/></template>
        </Button>
        <div class="actions"></div>
      </div>
    </div>
  </nav>
</template>

<script>
import IconZap from '~icons/feather/zap'
export default {
  components: {IconZap},
}
</script>

<style lang="scss" scoped>
@import '../assets/sass/resources';
nav{
  display:flex;
  width:100%;
  flex-direction:column;
  @include unselectable;

  .primary-nav{
    @include pad_lr;
    height:72px;
    display:flex;
    align-items:center;
    border-bottom:1px solid $outlines;
    justify-content:space-between;

    >div{
      display:flex;
      align-items:center;
    }
  }
}
</style>
