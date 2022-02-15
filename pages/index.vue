<template>
  <div class="dashboard">
    <section class="header">
      <div class="text">
        <h1>Welcome back, Olivia</h1>
        <h3>Track, manage and forecast your customers and orders.</h3>
      </div>
      <div class="actions">
        <Button name="Import">
          <template v-slot:icon><icon-upload-cloud class="icon-space ico" /></template>
        </Button>
        <Button class="primary" name="Add">
          <template v-slot:icon><icon-plus class="icon-space white ico" /></template>
        </Button>
      </div>
    </section>
    <section class="metric">
      <metric-item heading='Total customers' number=2,420 :change=40 />
      <metric-item heading='Members' number=1,210 :change=-10 />
      <metric-item heading='Active now' number=316 :change=20 />
    </section>
    <section>
      <Table />
    </section>
  </div>
</template>

<script>
import IconUploadCloud from "~icons/feather/upload-cloud";
import IconPlus from "~icons/feather/plus";
export default {
  name: 'UntitledUI',
  components:{
    IconUploadCloud,
    IconPlus,
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/sass/resources";
.dashboard{
  padding:72px 0;
  section{
    &:not(:last-child){margin-bottom:32px;}
  }
  >.header{
    display:flex;
    justify-content:space-between;

    > .text{
      h3{color: $grey;}
    }
    > .actions{
      display:flex;
      align-items:flex-start;
      > *:not(:last-child){
        margin-right:12px;
      }
    }
  }
  >.metric{
    display:grid;
    grid-template: 1fr / repeat(3,1fr);
    gap:24px;
    align-self:center;
    > div{
      max-width:390px;
    }
  }
}
</style>
