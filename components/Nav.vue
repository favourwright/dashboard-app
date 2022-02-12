<template>
  <nav>
    <div class="primary-nav">
      <div>
        <Logo />
        <MenuList
          :items="[
            { name: 'home' },
            { name: 'dashboard', isactive: true },
            { name: 'projects' },
            { name: 'tasks' },
            { name: 'reporting' },
            { name: 'users' },
          ]"
        />
      </div>
      <div>
        <Button name="Upgrade now">
          <template v-slot:icon><icon-zap class="btn-space" /></template>
        </Button>
        <div class="actions">
          <ul>
            <li><icon-settings class="grey" /></li>
            <li><icon-bell class="grey" /></li>
          </ul>
        </div>
        <Dropdown />
      </div>
    </div>
    <div class="secondary-nav">
      <MenuList
        :items="[
          { name: 'overview', isactive: true  },
          { name: 'notifications'},
          { name: 'analytics' },
          { name: 'saved reports' },
          { name: 'trade history' },
          { name: 'user reports' },
        ]"
      />
      <Search />
    </div>
  </nav>
</template>

<script>
import IconZap from "~icons/feather/zap";
import IconSettings from "~icons/feather/settings";
import IconBell from "~icons/feather/bell";
export default {
  components: { IconZap, IconSettings, IconBell },
}
</script>

<style lang="scss" scoped>
@import "../assets/sass/resources";
nav {
  display: flex;
  width: 100%;
  flex-direction: column;
  @include unselectable;

  .primary-nav {
    @include pad_lr;
    height: 72px;
    display: flex;
    align-items: center;
    border-bottom: 1px solid $outlines;
    justify-content: space-between;

    > div {
      display: flex;
      align-items: center;
      height:40px;
      > *:not(:last-child){
        margin-right:16px;
      }
      > *{
        height:100%;
      }
    }
  }
  .actions{
    ul{
      display:flex;
      align-items:center;
      height:100%;
      li{
        display:flex;
        height:100%;
        align-items:center;
        list-style: none;
        padding:10px;
        cursor:pointer;
      }
    }
  }
  .secondary-nav {
    @include pad_lr;
    height: 64px;
    display: flex;
    align-items: center;
    border-bottom: 1px solid $outlines;
    justify-content: space-between;
  }
}
</style>
