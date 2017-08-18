<template>
    <div>
        <h2>联系方式</h2>
        <el-form>
          <div v-for="(item,index) in items">
            <el-form-item label="电话">
                <el-input size="small" v-model="items[index].phone"></el-input>
            </el-form-item>
            <el-form-item label="邮箱">
                <el-input size="small" v-model="items[index].mail"></el-input>
            </el-form-item>
            <el-form-item label="QQ">
                <el-input size="small" v-model="items[index].qq" v-on:input="fn"></el-input>
            </el-form-item>
            <el-form-item label="其他联系方式">
                <el-input size="small" class="scroll" type="textarea" :autosize="{ minRows: 2}" placeholder="请输入内容" v-model="items[index].other">
                </el-input>
            </el-form-item>
          </div>
        </el-form>
    </div>
</template>
<script>
export default {
  props: ['items'],
  methods: {
    fn: function(){
      console.log(this.items)
    }
  }
}
</script>