<template>
  <div class="dashboard">
    <section class="header">
      <div class="text">
        <h1>Welcome back, Olivia</h1>
        <h3>Track, manage and forecast your customers and orders.</h3>
      </div>
      <div class="actions">
        <Button name="Import">
          <template #icon><icon-upload-cloud class="ico" /></template>
        </Button>
        <Button name="Add" css="primary">
          <template #icon><icon-plus class="white ico" /></template>
        </Button>
      </div>
    </section>
    <section class="metric">
      <metric-item
        v-for="(each,i) in metric_data"
        :key="i"
        :heading=each.heading
        :number=each.number
        :change=each.change
        :plot=each.plot
      />
    </section>
    <section>
      <Filters />
      <Table />
      <Pagination />
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
  },
  data(){
    return {
      metric_data:[
        {
          heading:'Total customers',
          number:'2,420',
          change:40,
          plot:{
            points:[1, 50, 26, 101, 100],
            timeline:[
              "2018-09-19T00:00:00.000Z",
              "2018-09-19T01:30:00.000Z",
              "2018-09-19T02:30:00.000Z",
              "2018-09-19T03:30:00.000Z",
              "2018-09-19T03:40:00.000Z"
            ]
          },
        },
        {
          heading:'Members',
          number:'1,210',
          change:-10,
          plot:{
            points:[100, 26, 50, 2, 1],
            timeline:[
              "2018-09-19T00:00:00.000Z",
              "2018-09-19T01:30:00.000Z",
              "2018-09-19T02:30:00.000Z",
              "2018-09-19T03:30:00.000Z",
              "2018-09-19T03:40:00.000Z"
            ]
          },
        },
        {
          heading:'Active now',
          number:'316',
          change:20,
          plot:{
            points:[1, 50, 26, 101, 100],
            timeline:[
              "2018-09-19T00:00:00.000Z",
              "2018-09-19T01:30:00.000Z",
              "2018-09-19T02:30:00.000Z",
              "2018-09-19T03:30:00.000Z",
              "2018-09-19T03:40:00.000Z"
            ]
          },
        },
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/sass/resources";
.dashboard{
  padding:72px 0;
  section{
    @include pad_lr;
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
    grid-template-columns: repeat(auto-fit, minmax(340px,1fr));
    grid-template-rows: auto;
    gap:24px;
  }
}
</style>
