<template>
  <div id="app">
      <Topbar class="topbar"></Topbar>
      <main>   
        <Editor class="editor"></Editor>
        <Preview class="preview"></Preview>
      </main>  
  </div>
</template>

<script>
import Topbar from './components/Topbar'
import Editor from './components/Editor'
import Preview from './components/Preview'

export default {
  name: 'app',
  components: {
  Topbar, Editor, Preview
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
  background: pink;
}
main{
  background: #ccc;
  display: flex;
  flex: 1;
  .editor{
    width: 200px;
  }
  .preview{
    background: orange;
    flex: 1;
    height: 100%;
  }
}

</style>
