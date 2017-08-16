<template>
    <div>
        <h2>工作经历</h2>
        <el-form>
          <div class="company" v-for="(company,index) in companyHistory">
            <el-form-item label="公司">
              <el-input v-model="companyHistory.company"></el-input>
            </el-form-item>
            <el-form-item label="工作内容">
              <el-input v-model="companyHistory.content"></el-input>
            </el-form-item>
            <i class="el-icon-delete" v-on:click="delateCompanyHistory(index)"></i>
          </div>
        </el-form>
        <el-button type="primary" v-on:click="addCompanyHistory">添加工作经历</el-button>
    </div>
</template>
<script>
export default {
  props: ['companyHistory'],
  methods:{
    addCompanyHistory(){
      this.companyHistory.push({
        company:'',content:''
      })
    },
    delateCompanyHistory(index){
      this.companyHistory.splice(index, 1)
    }
  }
}
</script>

