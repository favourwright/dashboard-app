<template>
  <nav>
    <div class="primary-nav">
      <div>
        <Logo />
        <menu-list
          :items="primary_menu_items"
          :can_wrap="true"
        />
      </div>
      <icon-menu class="burger ico-lg" />
      <div>
        <Button name="Upgrade now">
          <template #icon><icon-zap class="ico" /></template>
        </Button>
        <div class="actions">
          <ul>
            <li><icon-settings class="grey ico" /></li>
            <li><icon-bell class="grey ico" /></li>
          </ul>
        </div>
        <Dropdown />
      </div>
    </div>
    <div class="secondary-nav">
      <menu-list :items="secondary_menu_items" />
      <Search />
    </div>
  </nav>
</template>

<script>
import IconZap from "~icons/feather/zap";
import IconSettings from "~icons/feather/settings";
import IconBell from "~icons/feather/bell";
import IconMenu from "~icons/feather/menu";
export default {
  components: { IconZap, IconSettings, IconBell, IconMenu },
  data(){
    return {
      primary_menu_items:[
        { name: 'home' },
        { name: 'dashboard', isactive: true },
        { name: 'projects' },
        { name: 'tasks' },
        { name: 'reporting' },
        { name: 'users' },
      ],
      secondary_menu_items:[
        { name: 'overview', isactive: true  },
        { name: 'notifications'},
        { name: 'analytics' },
        { name: 'saved reports' },
        { name: 'trade history' },
        { name: 'user reports' },
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/sass/resources";
nav {
  width: 100%;
  position:fixed;
  top:0;
  background:#fff;
  z-index:10;
  @include unselectable;

  .primary-nav {
    @include pad_lr;
    min-height: 72px;
    display: flex;
    align-items: center;
    border-bottom: 1px solid $outlines;
    justify-content: space-between;

    .burger{display:none;}
    @mixin mobile{
      ul{
        display:none;
      }
      div:nth-of-type(2){
        display:none;
      }
      width:100%;
      .burger{
        display:block;
      }
    }
    @include sm{@include mobile;}
    @include md{@include mobile;}
    @include lg{@include mobile;}

    > div {
      display: flex;
      align-items: center;
      min-height:40px;
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
    min-height: 64px;
    width:100%;
    display: flex;
    align-items: center;
    border-bottom: 1px solid $outlines;
    justify-content: space-between;
    @mixin mobile{
      display:none;
    }
    @include sm{@include mobile}
    @include md{@include mobile}
    @include lg{@include mobile}
  }
}
</style>
