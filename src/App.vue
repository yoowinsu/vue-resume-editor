<template>
  <div id="app" v-bind:class="{previewMode: previewMode}">
      <Topbar class="topbar" v-on:preview="preview"/>
      <main>   
        <Editor v-bind:resume="resume" class="editor"/>
        <Preview v-bind:resume="resume" class="preview"/>
      </main>
      <el-button id="exit-preview" :plain="true" size="small" type="success" v-on:click="exitPreview">
        Exit
      </el-button>
      <el-button id="print" :plain="true" size="small" type="success" v-on:click="print">
        打印简历
      </el-button>
  </div>
</template>

<script>
import Topbar from './components/Topbar'
import Editor from './components/Editor'
import Preview from './components/Preview'
import Login from './components/Login'

export default {
  name: 'app',
  data(){
    return{
      previewMode: false,
      resume: {
        profile: {
          name: '',
          sex: '',
          city: '',
          birthYear: '',
          birthMonth: ''
        },
        companyHistory: [
          {company: '',timeStart: '',timeEnd: '',job: '',content: ''}
        ],
        educationHistory: [
          {school: '',durationStart: '',durationEnd: '',degree: '',major: '',content: ''}
        ],
        skill: [
          {list: ''}
        ],
        project: [
          {name: '',timeStart: '',timeEnd: '',content: ''}
        ],
        yourself:{content: ''},
        call: [
          {phone: '',mail:'',qq:'',wechat: '',other:''}
        ]
      }
    }
  },
  components: {
    Topbar, Editor, Preview, Login
  },
  methods: {
    preview(){
      this.previewMode = true
    },
    exitPreview(){
      this.previewMode = false
    },
    print(){
      window.print()
    }
  }
}
</script>

<style lang='scss'>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100vh;
  display: flex;
  flex-direction: column;
}
.topbar{
  box-shadow: 0 0 3px hsla(0, 0, 0, .6);
  position: relative;
  z-index: 1;
}

.icon {
    width: 1em; height: 1em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
}
#app main{
  background: #ddd;
  display: flex;
  flex: 1;
  .editor{
    background: #fff;
    width: 40vw;
    min-width: 32em;
    margin: 16px 8px 16px 16px;
    box-shadow: 0 0 3px hsla(0, 0, 0, .6);
    border-radius: 5px;
    overflow: hidden;
  }
  .preview{
    background: #fff;
    flex: 1;
    min-width: 300px;
    margin: 16px 16px 16px 8px;
    box-shadow: 0 0 3px hsla(0, 0, 0, .6);
    border-radius: 5px;
    overflow: auto;
  }
  &:hover+.previewMode #exit-preview{
    display: none;
  }
}

.previewMode{
  #topbar{
    display: none;
    color: #48576A;
  }
  #editor{
    display: none;
    color: #48576A;
  }
  #preview{
    max-width: 700px;
    margin: 20px auto;
    .bg{
      display: none;
    }
    &:hover div.bg{
      display: none;
    }
  }
  #exit-preview{
    display: block;
    position: fixed;
    top: 12px;
    left: 12px;
  }
  #print{
    display: block;
    position: fixed;
    top: 44px;
    left: 12px;
    margin-left: 0;
  }
}

#exit-preview,#print{
  display: none;
}

@media print {
  .previewMode #print,.previewMode #exit-preview{
    display: none;
  }
}
</style>
