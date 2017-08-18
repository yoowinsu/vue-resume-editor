<template>
    <div>
        <h2>教育经历</h2>
        <el-form>
          <div class="item" v-for="(item,index) in items">
            <el-form-item label="学校">
                <el-input size="small" v-model="items[index].school"></el-input>
            </el-form-item>
            <el-form-item label="时间">
                <el-input size="small" v-model="items[index].duration"></el-input>
            </el-form-item>
            <el-form-item label="学位">
                <el-input size="small" v-model="items[index].degree"></el-input>
            </el-form-item>
            <el-form-item label="专业">
                <el-input size="small" v-model="items[index].major"></el-input>
            </el-form-item>
            <el-form-item label="奖项">
                <el-input size="small" class="scroll" type="textarea" :autosize="{ minRows: 4}" placeholder="请输入内容" v-model="items[index].content">
                </el-input>
            </el-form-item>
            <i class="el-icon-delete" v-on:click="removeItem(index)"></i>
          </div>
        </el-form>
        <el-button class="add-block" :plain="true" type="success" size="small" v-on:click="addItem">添加</el-button>
    </div>
</template>
<script>
export default {
  props: ['items'],
  methods:{
    addItem(){
      this.items.push({
        school: '',duration: '',degree: '',major: '',content: ''
      })
    },
    removeItem(index){
      this.items.splice(index, 1)
    }
  }
}
</script>
