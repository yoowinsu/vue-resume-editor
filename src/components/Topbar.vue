<template>
    <div id="topbar">
        <div class="logo">
            <a href="#">
                <svg class="logo-icon" aria-hidden="true">
                    <use v-bind:xlink:href="`#icon-gerenjianlizitisheji`"></use>
                </svg>
            </a>
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
    font-size: 26px;
    font-family: sans-serif;
    .logo-icon{
        height: 40px;
        position: absolute;
        left: 20px;
        top: 6px;
        width: 80px;
    }
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
