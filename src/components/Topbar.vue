<template>
    <div id="topbar">
        <div class="logo">
            <a href="#">Resume</a>
        </div>
        <div class="actions">
            <el-button :plain="true" type="success" size="small">登录</el-button>
            <el-button :plain="true" type="success" size="small">注册</el-button>
            <el-button type="success" size="small" v-on:click="preview">预览</el-button>
        </div>
    </div>
</template>


<style lang='scss'>
#topbar{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 12px 18px 12px 22px;
    font-size: 20px;
}
#topbar .logo a{
    color: #888;
    display: inline-block;
    font-size: 22px;
    font-family: 'Comic Sans MS', sans-serif;
}
#topbar .logo a:hover{
    text-shadow: 0 0 1px rgba(0,0,0,.4);
    transition: all .5s;
}
</style>

<script>
export default {
  methods: {
      preview(){
          this.$emit('preview')
      }
  }
}
</script>
