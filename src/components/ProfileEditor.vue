<template>
    <div>
        <h2>基本信息</h2>
        <el-form>
          <el-form-item label="姓名">
            <el-input v-model="profile.name"></el-input>
          </el-form-item>
          <el-form-item label="性别">
            <el-input v-model="profile.sex"></el-input>
          </el-form-item>
          <el-form-item label="所在城市">
            <el-input v-model="profile.city"></el-input>
          </el-form-item>
          <el-form-item label="生日">
            <el-input v-model="profile.birth"></el-input>
          </el-form-item>
        </el-form>
    </div>
</template>

<script>
export default {
  props: ['profile']
}
</script>
