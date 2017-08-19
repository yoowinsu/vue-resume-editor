<template>
    <div>
        <h2>项目经验</h2>
        <el-form>
          <div class="item" v-for="(item,index) in items">
            <el-form-item label="项目名称">
              <el-input size="small" v-model="items[index].name"></el-input>
            </el-form-item>
            <el-form-item label="时间">
              <el-input size="small" v-model="items[index].timeStart">
                <el-select v-model="items[index].timeStart" slot="prepend" placeholder="起始时间">
                  <el-option v-for="start in times" v-bind:label="start" v-bind:value="start"></el-option>
                </el-select>
              </el-input>
              <span class="to">至</span>
              <el-input size="small" v-model="items[index].timeEnd" placeholder="结束时间">
                <el-select v-model="items[index].timeEnd" slot="prepend">
                  <el-option v-for="end in times" v-bind:label="end" v-bind:value="end"></el-option>
                </el-select>
              </el-input>
            </el-form-item>
            <el-form-item label="项目内容">
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
          name: '',timeStart: '',timeEnd: '',content: ''
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
      for(let i = nowYear;i>nowYear-20;i--){
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