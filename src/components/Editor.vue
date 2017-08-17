<template>
  <div id="editor">
    <nav>
      <ol>
        <li v-for="i in [0,1,2,3,4,5,6]" v-bind:class="{active: currentTab === i}" v-on:click="currentTab = i">
            <svg class="icon" aria-hidden="true">
              <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
            </svg>
        </li>
      </ol>
    </nav>
    <ol class="panels">
      <li v-bind:class="{active: currentTab === 0}">
        <ProfileEditor v-bind:profile="resume.profile"/>
      </li>
      <li v-bind:class="{active: currentTab === 1}">
        <CompanyHistoryEditor v-bind:items="resume.companyHistory"/>
      </li>
      <li v-bind:class="{active: currentTab === 2}">
        <EducationHistoryEditor v-bind:items="resume.educationHistory"/>
      </li>
      <li v-bind:class="{active: currentTab === 3}">
        <h2>自我评价</h2>
        <el-form>
            <el-input type="textarea" :autosize="{ minRows: 4}" placeholder="请输入内容" v-model="resume.yourself.content">
            </el-input>
        </el-form>
      </li>
      <li v-bind:class="{active: currentTab === 4}">
        <SkillEditor v-bind:items="resume.skill"/>
      </li>
      <li v-bind:class="{active: currentTab === 5}">
        <ProjectEditor v-bind:items="resume.project"/>
      </li>
      <li v-bind:class="{active: currentTab === 6}">
        <CallEditor v-bind:items="resume.call"/>
      </li>
    </ol>
  </div>
</template>

<script>
import ProfileEditor from './ProfileEditor'
import CompanyHistoryEditor from './CompanyHistoryEditor'
import EducationHistoryEditor from './EducationHistoryEditor'
import CallEditor from './CallEditor'
import SkillEditor from './SkillEditor'
import ProjectEditor from './ProjectEditor'

export default {
  props:['resume'],
  data(){
    return{
      currentTab: 0,
      icons: ['jibenxinxi','WORK','xueli','moban8ziwopingjia','jishu1','02','iconwolxwm']
    }
  },
  components: {
    ProfileEditor, CompanyHistoryEditor, EducationHistoryEditor, CallEditor, SkillEditor, ProjectEditor
  }
}
</script>


<style lang='scss'>
.panels li::-webkit-scrollbar,.scroll::-webkit-scrollbar {
    width: 4px; /*垂直方向滚动条宽度*/
}
      /*滚动条轨道*/
.panels li::-webkit-scrollbar-track,.scroll::-webkit-scrollbar-track {
    background-color: #eee;
} 
      /*滑块*/
.panels li::-webkit-scrollbar-thumb,.scroll::-webkit-scrollbar-thumb {
    background-color: #C2C1C3;
    border-radius: 2px;
}

#editor{
  display: flex;
  min-height: 100px;
  nav {
    background: #222;
    width: 60px;
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
      padding: 0 20px;
      display: none;
      overflow: auto;
      height: 100%;
      &.active{
        display: block;
      }
      h2{
        margin: 10px 0;
      }
      .item{
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
      .add-block{
        margin: 10px 0;
      }
    }
  }
}

</style>