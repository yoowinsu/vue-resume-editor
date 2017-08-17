<template>
    <div id="topbar">
        <div class="logo">
            Resumer
        </div>
        <div class="actions">
            <el-button type="primary">登录</el-button>
            <el-button>注册</el-button>
            <el-button type="primary" v-on:click="preview">预览</el-button>
        </div>
    </div>
</template>


<style lang='scss'>
#topbar{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 16px;
    font-size: 20px;
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
