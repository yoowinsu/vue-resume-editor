<template>
  <div id="editor">
    <nav>
      <ol>
        <li v-for="i in [0,1,2,3,4,5]" v-bind:class="{active: currentTab === i}" v-on:click="currentTab = i">
            <svg class="icon" aria-hidden="true">
              <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
            </svg>
        </li>
      </ol>
    </nav>
    <ol class="panels">
      <li v-bind:class="{active: currentTab === 0}">
        <ProfileEditor v-bind:profile="profile"/>
      </li>
      <li v-bind:class="{active: currentTab === 1}">
        <CompanyHistoryEditor v-bind:companyHistory="companyHistory"/>
      </li>
      <li v-bind:class="{active: currentTab === 2}">
        <h2>教育经历</h2>
      </li>
      <li v-bind:class="{active: currentTab === 3}">
        <h2>兴趣爱好</h2>
      </li>
      <li v-bind:class="{active: currentTab === 4}">
        <h2>技能清单</h2>
      </li>
      <li v-bind:class="{active: currentTab === 5}">
        <h2>项目列表</h2>
      </li>
    </ol>
  </div>
</template>

<script>
import CompanyHistoryEditor from './CompanyHistoryEditor'
import ProfileEditor from './ProfileEditor'

export default {
  components: {
    ProfileEditor, CompanyHistoryEditor
  },
  data(){
    return{
      currentTab: 0,
      icons: ['xinxi','WORK','xueli','heartrate','jishu1','02'],
      profile: {
        name: '',
        city: '',
        birth: ''
      },
      companyHistory: [
        {company: '',content: ''}
      ]
    }
  },
  methods: {

  }
}
</script>


<style lang='scss'>
#editor{
  display: flex;
  min-height: 100px;
  nav {
    background: #222;
    width: 80px;
    height: 100%;
    ol li{
      text-align: center;
      padding: 16px 0;
      .icon {
        width: 24px;
        height: 24px;
        fill: #fff;
      }
      &.active{
        background: #fff;
        .icon{
          fill: #000;
        }
      } 
    }
  }
  .panels{
    flex: 1;
    text-align: center;
    li{
      padding: 20px;
      display: none;
      overflow: auto;
      height: 100%;
      &::-webkit-scrollbar {
        width: 4px; /*垂直方向滚动条宽度*/
      }
      /*滚动条轨道*/
      &::-webkit-scrollbar-track {
        background-color: #eee;
      } 
      /*滑块*/
      &::-webkit-scrollbar-thumb {
        background-color: #C2C1C3;
        border-radius: 2px;
      }
      &.active{
        display: block;
      }
      .company{
        padding: 0 6px 6px;
        position: relative;
        margin: 4px 0;
        &:hover{
          box-shadow: 0 0 3px 1px rgba(0, 0, 0, .3);
        }
        &:hover .el-icon-delete{
          display: block;
        }
        .el-icon-delete{
          display: none;
          position: absolute;
          right: 4px;
          top: 4px;
          cursor: pointer;
        }
      }
    }
  }
}

</style>