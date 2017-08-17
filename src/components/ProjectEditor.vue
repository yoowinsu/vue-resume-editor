<template>
    <div>
        <h2>项目经验</h2>
        <el-form>
          <div class="item" v-for="(item,index) in items">
            <el-form-item label="项目名称">
              <el-input size="small" v-model="items[index].name"></el-input>
            </el-form-item>
            <el-form-item label="时间">
              <el-input size="small" v-model="items[index].time"></el-input>
            </el-form-item>
            <el-form-item label="项目介绍">
                <el-input size="small" type="textarea" :autosize="{ minRows: 4}" placeholder="请输入内容" v-model="items[index].content">
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
          name: '',time: '',content: ''
        })
    },
    removeItem(index){
      this.items.splice(index, 1)
    }
  }
}
</script>