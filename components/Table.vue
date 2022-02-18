<template>
<div class="table">
  <div class="card">
    <div class="table-concept">
      <table>
        <thead>
          <tr>
            <th><Checkbox name='disseect' /></th>
            <th>Company</th>
            <th>License use</th>
            <th>Status</th>
            <th>Users</th>
            <th>About</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="n in 10" :key="n">
            <td>
              <Checkbox :name='`row${n}`' />
            </td>
            <td v-for="i in 5" :key="i">This is Item number {{`${i} in ${n}`}}</td>
          </tr>
        </tbody>
      </table>
      <div class="pagination">
        <label>Previous</label>
        <label>Next</label>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
@import '../assets/sass/resources';
.table{
  border:1px solid $outlines;
  border-radius:8px;
  box-shadow: 0 4px 8px -2px rgba(16, 24, 40, 0.1),
              0 2px 4px -2px rgba(16, 24, 40, 0.06);
  overflow:hidden;
}

$pagination-background-color: #8f8f8f;
$pagination-label-background-color: $pagination-background-color;
$pagination-label-active-color: #ffffff;
$pagination-label-active-background-color: darken($pagination-background-color, 15%);
$pagination-label-disabled-color: #ffffff;
$pagination-label-disabled-background-color: lighten($pagination-background-color, 15%);

.card {
  background-color: #ffffff;
  width: 100%;
  max-width: 100%;
  max-height: 100%;
  display: flex;
  flex-direction: column;
  overflow:hidden;
}

.table-concept {
  width: 100%;
  height: 100%;
  max-height: 100%;
  box-sizing: border-box;
  overflow: auto;
  table {
    background-color: $grey_light_1;
    font-size: 14px;
    border-collapse: collapse;
    width:100%;
    display: table;
    tr {
      &:last-child {
        td {
          border-bottom: 0;
        }
      }
      th, td {
        text-align: left;
        padding: 16px 24px;
        box-sizing: border-box;
      }
      // heading area
      th {
        background:#fff;
        font-size:12px;
        font-weight: 500;
        border-bottom: solid 1px $divider;
        position: sticky;
        top: 0;
        &:nth-child(2){ padding-left:0; }
      }
      // table content area
      td {
        border-left: 0;
        border-right: 0;
        white-space: nowrap;
      }
    }
    tbody tr {
      transition: background-color 150ms ease-out;
      &:nth-child(2n) {
        background-color: #fff;
      }
      > td:nth-child(2){
        padding-left:0;
      }
      // &:hover {
      //   background-color: #F9FAFB;
      // }
    }
  }
  .pagination {
    background-color: #fff;
    width: 100%;
    display: flex;
    position: sticky;
    bottom: 0;
    left: 0;
    & > label {
      padding: 10px;
      cursor: pointer;
    }
  }
}
</style>
