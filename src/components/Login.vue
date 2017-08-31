<template>
  <div>
    <ol>
      <li>
        <button>登录</button>
      </li>
      <li>
        <button>注册</button>
      </li>
    </ol>
    <ol>
      <li>
        <el-form>
          <el-form-item label="用户名">
            <el-input size="small" v-model="profile.name"></el-input>
          </el-form-item>
          <el-form-item label="密码">
            <el-input size="small" v-model="profile.name"></el-input>
          </el-form-item>
        </el-form>
      </li>
      <li>
        <el-form>
          <el-form-item label="用户名">
            <el-input size="small" v-model="profile.name"></el-input>
          </el-form-item>
          <el-form-item label="密码">
            <el-input size="small" v-model="profile.name"></el-input>
          </el-form-item>
          <el-form-item label="确认密码">
            <el-input size="small" v-model="profile.name"></el-input>
          </el-form-item>
        </el-form>
      </li>
    </ol>
  </div>
</template>

<script>
export default {
  
}
</script>

