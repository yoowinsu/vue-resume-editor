<template>
    <div>
        <h2>基本信息</h2>
        <el-form>
          <el-form-item label="姓名">
            <el-input size="small" v-model="profile.name"></el-input>
          </el-form-item>
          <el-form-item label="性别">
            <el-radio-group size="small" fill="#13CE66" text-color="#fff" v-model="profile.sex">
              <el-radio-button label="男">男</el-radio-button>
              <el-radio-button label="女">女</el-radio-button >
            </el-radio-group>
          </el-form-item>
          <el-form-item label="所在城市">
            <el-input size="small" v-model="profile.city"></el-input>
          </el-form-item>
          <el-form-item label="生日">
            <el-input size="small" v-model="profile.birthYear">
                <el-select v-model="profile.birthYear" slot="prepend">
                  <el-option v-for="year in allYears" size="small" v-bind:label="year" v-bind:value="year+'年'" placeholder="年份"></el-option>
                  <template slot="append">年</template>
                </el-select>
              </el-input>
              <el-input size="small" v-model="profile.birthMonth">
                <el-select v-model="profile.birthMonth" slot="prepend">
                  <el-option v-for="month in [1,2,3,4,5,6,7,8,9,10,11,12]" v-bind:label="month" v-bind:value="month+'月'" placeholder="月份"></el-option>
                  <template slot="append">月</template>
                </el-select>
              </el-input>
          </el-form-item>
        </el-form>
    </div>
</template>

<script>
export default {
  props: ['profile'],
  computed: {
    allYears: function (){
      let arr = []
      let now = new Date().getFullYear()
      for(let i = now;arr.length<60;i--){
        arr.push(i)
      }
      return arr
    }
  }
}
</script>
