<template>
    <div>
        <h2>技能清单</h2>
        <el-form>
          <div class="item" v-for="(item,index) in items">
            <el-form-item label="列表">
                <el-input size="small" class="scroll" type="textarea" :autosize="{ minRows: 4}" placeholder="请输入内容" v-model="items[index].list">
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
        list: ''
      })
    },
    removeItem(index){
      this.items.splice(index, 1)
    }
  }
}
</script>