<template>
    <div>
        <h2>工作经历</h2>
        <el-form>
          <div class="item" v-for="(item,index) in items">
            <el-form-item label="公司">
              <el-input size="small" v-model="items[index].company"></el-input>
            </el-form-item>
            <el-form-item label="在职时间">
              <el-input size="small" v-model="items[index].time">
                <el-select v-model="items[index].timeStart" slot="prepend" placeholder="年份">
                  <el-option v-for="start in times" v-bind:label="start" v-bind:value="start"></el-option>
                  <template slot="append">年</template>
                </el-select>
              </el-input>
              <el-input size="small" v-model="items[index].time">
                <el-select v-model="items[index].timeEnd" slot="prepend" placeholder="月份">
                  <el-option v-for="end in times" v-bind:label="end" v-bind:value="end"></el-option>
                  <template slot="append">月</template>
                </el-select>
              </el-input>
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
    },
    removeItem(index){
      this.items.splice(index, 1)
    }
  },
  computed: {
    times: function (){
      let arr = []
      let nowYear = new Date().getFullYear()
      let nowMonth = new Date().getMonth()+1
      for(let i = nowYear;arr.length<20;i--){
        for(let j=12;j<12;j--){
          if(j.toString().length === 1){
            arr.push(i+'年0'+j+'月')
          }else{
            arr.push(i.toString()+'年'+j+'月')
          }
        }
      }
      // for(i=0;i<12-nowMonth;i++){
      //   arr.shift()
      // }
      return arr
    }
  }
}
</script>

