<template>
  <div id="app" v-bind:class="{previewMode: previewMode}">
      <Topbar class="topbar" v-on:preview="preview"/>
      <main>   
        <Editor v-bind:resume="resume" class="editor"/>
        <Preview v-bind:resume="resume" class="preview"/>
      </main>
      <el-button id="exit-preview" size="small" type="success" v-on:click="exitPreview"><svg class="icon" fill="#fff" aria-hidden="true">
              <use v-bind:xlink:href="'#icon-exit'"></use>
            </svg>Exit</el-button>
  </div>
</template>

<script>
import Topbar from './components/Topbar'
import Editor from './components/Editor'
import Preview from './components/Preview'

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
          {company: '',timeStart: '',timeEnd: '',job: '',content: ``}
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
          {phone: '',mail:'',qq:'',other:''}
        ]
      }
    }
  },
  components: {
    Topbar, Editor, Preview
  },
  methods: {
    preview(){
      this.previewMode = true
    },
    exitPreview(){
      this.previewMode = false
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
main{
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
    margin: 16px 16px 16px 8px;
    box-shadow: 0 0 3px hsla(0, 0, 0, .6);
    border-radius: 5px;
    overflow: auto;
  }
  &:hover+.previewMode #exit-preview{
    display: none;
  }
}

.previewMode #topbar{
  display: none;
}
.previewMode #editor{
  display: none;
}
.previewMode #preview{
  max-width: 700px;
  margin: 20px auto;
}

#exit-preview{
  display: none;
}
.previewMode #exit-preview{
  display: block;
  position: fixed;
  top: 12px;
  left: 12px;
}
</style>
