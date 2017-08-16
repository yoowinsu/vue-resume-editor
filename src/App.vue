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
  background: #ccc;
  display: flex;
  flex: 1;
  .editor{
    background: #fff;
    width: 40em;
    margin: 16px 8px 16px 16px;
    box-shadow: 0 0 3px hsla(0, 0, 0, .6);
    border-radius: 5px;
  }
  .preview{
    background: #fff;
    flex: 1;
    margin: 16px 16px 16px 8px;
    box-shadow: 0 0 3px hsla(0, 0, 0, .6);
    border-radius: 5px;
  }
}

</style>
