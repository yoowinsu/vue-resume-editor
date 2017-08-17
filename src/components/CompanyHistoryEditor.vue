<template>
    <div>
        <h2>工作经历</h2>
        <el-form>
          <div class="item" v-for="(item,index) in items">
            <el-form-item label="公司">
              <el-input size="small" v-model="items[index].company"></el-input>
            </el-form-item>
            <el-form-item label="时间">
              <el-input size="small" v-model="items[index].time"></el-input>
            </el-form-item>
            <el-form-item label="职位">
              <el-input size="small" v-model="items[index].job"></el-input>
            </el-form-item>
            <el-form-item label="工作内容">
                <el-input size="small" class="scroll" type="textarea" :autosize="{ minRows: 4}" placeholder="请输入内容" v-model="items[index].content">
                </el-input>
            </el-form-item>
            <i class="el-icon-delete" v-on:click="removeItem(index)"></i>
          </div>
        </el-form>
        <el-button class="add-block" :plain="true" type="success" size="small" v-on:click="addItem">添加工作经历</el-button>
    </div>
</template>
<script>
export default {
  props: ['items'],
  methods:{
    addItem(){
      this.items.push({
        company:'',time: '',job: '',content:''
      })
      console.log(this.items)
    },
    removeItem(index){
      this.items.splice(index, 1)
    }
  }
}
</script>

