<template>
  <div class="card">
    <section>
      <h3 class="heading" v-text="heading"></h3>
      <option-dropdown />
    </section>
    <section>
      <main>
        <h1 v-text="number"></h1>
        <div class="change_n_text">
          <div>
            <icon-arrow-up v-if="change>0" stroke-width=2 class="green ico" />
            <icon-arrow-down v-else stroke-width=2 class="red ico" />
            <span :class="change>0?'green':'red'" v-text="Math.abs(change)+'%'"></span>
          </div>
          <div title="vs last month">vs last month</div>
        </div>
      </main>
      <div class="chart">
        <apexchart type="area" width="128" height="auto" stroke="1" :options="chartOptions" :series="series" />
      </div>
    </section>
  </div>
</template>

<script>
import IconArrowUp from "~icons/feather/arrow-up";
import IconArrowDown from "~icons/feather/arrow-down";
export default {
  props: {
    heading: String,
    number: String,
    change: Number,
    plot: Object
  },
  components:{
    IconArrowUp,
    IconArrowDown,
  },
  data(){
    return {
      series: [{
        name: 'series',
        data: this.plot.points
      }],
      chartOptions: {
        chart: {
          height: 100,
          type: 'area',
          sparkline: {
            enabled: true,
          },
        },
        dataLabels: {
          enabled: false
        },
        stroke: {
          curve: 'smooth',
          width: 2,
        },
        colors: this.change > 0 ? ['#12B76A'] : ['#F04438'],
        fill: {
          gradient: {
              shadeIntensity: 0.9,
          },
        },
        xaxis: {
          type: 'datetime',
          categories: this.plot.timeline
        },
        tooltip: {
          x: {
            format: 'dd/MM/yy HH:mm'
          },
        },
      },
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/sass/resources";
.card{
  min-height:176px;
  padding:24px;
  border:1px solid $outlines;
  border-radius:8px;
  overflow:hidden;
  box-shadow: 0 1px 2px 0 rgba(16, 24, 40, 0.06),
              0 1px 3px 0 rgba(16, 24, 40, 0.1);
  section{
    display:flex;
    justify-content:space-between;
    &:not(:last-child){margin-bottom:24px;}

    > main{
      margin-right:10px;
      max-width:50%;
      h1{
        margin-bottom:16px;
      }
      .change_n_text{
        display:flex;
        align-items:center;
        *{font-size:14px;font-weight:500;}
        *:not(:last-child){margin-right:8px;}
        > div:first-child{ @include flex; }
        .green{color:$green_dark;}
        .red{color:$red_dark;}
        > div:last-child{
          color:$grey;
          white-space: nowrap;
          overflow: hidden;
          text-overflow: ellipsis;
        }
      }
    }
  }
  h1{
    font-size:36px;
    font-weight:600;
  }
  .heading{
    font-size:16px;
    font-weight:500;
  }
}
</style>
