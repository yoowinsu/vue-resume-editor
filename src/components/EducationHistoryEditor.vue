<template>
    <div>
        <h2>教育经历</h2>
        <el-form>
          <div class="item" v-for="(item,index) in items">
            <el-form-item label="学校">
                <el-input size="small" v-model="items[index].school"></el-input>
            </el-form-item>
            <el-form-item label="时间">
              <el-input size="small" v-model="items[index].durationStart" placeholder="起始时间">
                <el-select v-model="items[index].durationStart" slot="prepend">
                  <el-option v-for="start in times" v-bind:label="start" v-bind:value="start"></el-option>
                </el-select>
              </el-input>
              <span class="to">至</span>
              <el-input size="small" v-model="items[index].durationEnd" placeholder="结束时间">
                <el-select v-model="items[index].durationEnd" slot="prepend">
                  <el-option v-for="end in times" v-bind:label="end" v-bind:value="end"></el-option>
                </el-select>
              </el-input>
            </el-form-item>
            <el-form-item label="学位">
                <el-input size="small" v-model="items[index].degree"></el-input>
            </el-form-item>
            <el-form-item label="专业">
                <el-input size="small" v-model="items[index].major"></el-input>
            </el-form-item>
            <el-form-item label="奖项及其他">
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
      console.log(this.items[0].content)
      this.items.push({
        school: '',durationStart: '',durationEnd: '',degree: '',major: '',content: ''
      })
    },
    removeItem(index){
      this.items.splice(index, 1)
    }
  },
  computed: {
    times: function () {
      let arr = []
      let nowYear = new Date().getFullYear()
      let nowMonth = new Date().getMonth()+1
      for(let i = nowYear;i>nowYear-40;i--){
        for(let j=12;j>0;j--){
          if(j.toString().length === 1){
            arr.push(i+'年0'+j+'月')
          }else{
            arr.push(i.toString()+'年'+j+'月')
          }
        }
      }
      for(let k=0;k<12-nowMonth;k++){
         arr.shift()
       }
      return arr
    }
  }
}
</script>
