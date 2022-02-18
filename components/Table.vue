<template>
<div class="table">
  <div class="card">
    <div class="table-concept">
      <table>
        <thead>
          <tr>
            <th><Checkbox name='disselect' :is_check_mark='false' /></th>
            <th>Company</th>
            <th>License use</th>
            <th>Status</th>
            <th>Users</th>
            <th>About</th>
            <th></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(each,i) in table_data" :key="i">
            <td>
              <Checkbox :name='`row-${i}`' :is_check_mark='true' />
            </td>
            <td class="flex">
              <Avatar :name='each.avatar' />
              <div class="company">
                <h2 v-text="each.name"></h2>
                <span v-text="each.web"></span>
              </div>
            </td>
            <td><Progress :progress="each.progress" /></td>
            <td><Badge :churned="each.status=='Churned'?true:false">{{each.status}}</Badge></td>
            <td><AvatarGroup :users="each.users" /></td>
            <td>
              <div class="about">
                <h2>{{each.about[0]}}</h2>
                <span>{{each.about[1]}}</span>
              </div>
            </td>
            <td>
              <div><icon-trash class="ico" /></div>
              <div><icon-edit class="ico" /></div>
            </td>
          </tr>
        </tbody>
      </table>
      <div class="pagination">
        <div class="action">
          <Button name="Previous" />
          <Button name="Next" />
        </div>
        <div class="details">Page 1 of 10</div>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import IconTrash from "~icons/feather/trash-2";
import IconEdit from "~icons/feather/edit-2";
export default {
  components:{
    IconTrash,IconEdit
  },
  data(){
    return {
      table_data:[
        {
          avatar:'catalog.png',
          name:'Catalog',web:'catalogapp.io',
          progress:80,
          status:'Customer',
          users:[
            "avatar.png",
            "download-4.png",
            "download-3.png",
            "download-12.png",
            "download-2.png",
            "5",
          ],
          about:['Content curating app','Brings all your news into one place'],
        },
        {
          avatar:'circooles.png',
          name:'Circooles',web:'getcirooles.com',
          progress:70,
          status:'Churned',
          about:['Design software','Super lightweight design app'],
          users:[
            "download-12.png",
            "download-9.png",
            "download-5.png",
            "download-11.png",
            "download-13.png",
            "8",
          ],
        },
        {
          avatar:'cmdr.png',
          name:'Command+R',web:'cmdr.ai',
          progress:40,
          status:'Customer',
          about:['Data prediction','AI and machine learning data'],
          users:[
            "download-13.png",
            "download-8.png",
            "download-6.png",
            "download-11.png",
            "download-7.png",
            "2",
          ],
        },
        {
          avatar:'hourglass.png',
          name:'Hourglass',web:'hourglass.app',
          progress:80,
          status:'Customer',
          about:['Productivity app','Time management and productivity'],
          users:[
            "download-2.png",
            "download-4.png",
            "download-10.png",
            "download-9.png",
            "download-8.png",
            "",
          ],
        },
        {
          avatar:'layers.png',
          name:'Layers',web:'getlayers.io',
          progress:30,
          status:'Churned',
          about:['Web app integrations','Connect web apps seamlessly'],
          users:[
            "download-3.png",
            "download-10.png",
            "download-8.png",
            "download-11.png",
            "download-13.png",
            "1",
          ],
        },
        {
          avatar:'quotient.png',
          name:'Quotient',web:'quotient.co',
          progress:20,
          status:'Customer',
          about:['Sales CRM','Web-based sales doc management'],
          users:[
            "download-2.png",
            "download-3.png",
            "download-8.png",
            "download-10.png",
            "download-6.png",
            "6",
          ],
        },
        {
          avatar:'sisyphus.png',
          name:'Sisyphus',web:'sisyphus.com',
          progress:40,
          status:'Customer',
          about:['Automation and workflow','Time tracking, invoicing and expenses'],
          users:[
            "download-9.png",
            "download-6.png",
            "download-5.png",
            "download-8.png",
            "download-12.png",
            "4",
          ],
        },
      ]
    }
  }

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
        &:first-child{
          position: sticky;
          z-index:1;
          max-width:60px;
          z-index:1;
          left: 0;
        }
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
      &:nth-child(odd) {
        background-color: $grey_light_1;
      }
      > td:nth-child(2){
        padding-left:0;
      }
      > td:first-child, >td:last-child{
        position: sticky;
        max-width:60px;
        z-index:1;
        background:inherit;
      }
      > td:first-child{
        left: 0;
      }
      > td:last-child {
        right: 0;
        max-width:100px;
        @include flex(center,center);
        > *{
          @include flex;
          min-height:40px;
          min-width:40px;
        }
      }
      // &:hover {
      //   background-color: #F9FAFB;
      // }
      .company{
        margin-left:12px;
      }
      .company,.about{
        h2,span{
          font-size:14px;
          font-weight:500;
          color: $xblack;
        }
        span{
          color:$grey;
        }
      }
    }
  }
  .flex{
    display:flex;
  }
  .pagination {
    @include flex(space-between);
    position: sticky;
    bottom: 0;
    left: 0;
    background-color: #fff;
    width: 100%;
    padding: 14px 24px;
    border-top: solid 1px $divider;
    .action{
      @include flex;
      > *{
        margin-right:12px;
      }
    }
  }
}
</style>
