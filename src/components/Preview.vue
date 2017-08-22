<template>
    <div id="preview" class="scroll" v-on:mouseenter="enter" v-on:mouseleave="leave">
        <div class="bg" v-bind:class="animation">
            <ul>
                <li v-for="i in [0,1,2,3,4,5]"
                v-bind:class="{active:themeTab === theme[i]}"
                v-on:click="themeTab = theme[i]">
                {{themeText[i]}}
                </li>
            </ul>
        </div>
        <div class="show" v-bind:class="themeTab">
            <section v-if="!isEmpty(resume.profile)">
                <h2 class="title">基本信息</h2>
                <p v-if="resume.profile.name"><span>姓名</span>：{{resume.profile.name}}</p>
                <p v-if="resume.profile.sex"><span>性别</span>：{{resume.profile.sex}}</p>
                <p v-if="resume.profile.city"><span>所在城市</span>：{{resume.profile.city}}</p>
                <p v-if="resume.profile.birthYear"><span>生日</span>：{{resume.profile.birthYear}}{{resume.profile.birthMonth}}</p>
            </section>
            <section v-if="filter(resume.companyHistory).length > 0">
                <h2 class="title">工作经历</h2>
                <ul>
                    <li v-for="companyHistory in filter(resume.companyHistory)">
                        <p v-if="companyHistory.company"><span>公司</span>：{{companyHistory.company}}</p>
                        <p v-if="companyHistory.timeStart"><span>在职时间</span>：{{companyHistory.timeStart}}——{{companyHistory.    timeEnd}}</p>
                        <p v-if="companyHistory.job"><span>职位</span>：{{companyHistory.job}}</p>
                        <p v-if="companyHistory.content"><span>工作内容</span>：{{companyHistory.content}}</p>
                    </li>
                </ul>
            </section>
            <section v-if="filter(resume.educationHistory).length > 0">
                <h2 class="title">教育经历</h2>
                <ul>
                    <li v-for="educationHistory in filter(resume.educationHistory)">
                        <p v-if="educationHistory.school"><span>学校</span>：{{educationHistory.school}}</p>
                        <p v-if="educationHistory.durationStart"><span>时间</span>：{{educationHistory.durationStart}}——{{educationHistory.durationEnd}}</p>
                        <p v-if="educationHistory.degree"><span>学位</span>：{{educationHistory.degree}}</p>
                        <p v-if="educationHistory.major"><span>专业</span>：{{educationHistory.major}}</p>                    
                        <p v-if="educationHistory.content"><span>奖项及其他</span>：{{educationHistory.content}}</p>
                    </li>
                </ul>
            </section>
    
            <section v-if="!isEmpty(resume.yourself)">
                <h2 class="title">自我评价</h2>
                <p v-if="resume.yourself.content">{{resume.yourself.content}}</p>
            </section>
    
            <section v-if="filter(resume.skill).length > 0">
                <h2 class="title">技能清单</h2>
                <ul>
                    <li v-for="skill in filter(resume.skill)">
                        <p v-if="skill.list">{{skill.list}}</p>
                    </li>
                </ul>
            </section>
    
            <section v-if="filter(resume.project).length > 0">
                <h2 class="title">项目经验</h2>
                <ul>
                    <li v-for="project in filter(resume.project)">
                        <p v-if="project.name"><span>项目名称</span>：{{project.name}}</p>
                        <p v-if="project.timeStart"><span>时间</span>：{{project.timeStart}}——{{project.timeEnd}}</p>                   
                        <p v-if="project.content"><span>项目内容</span>：{{project.content}}</p>
                    </li>
                </ul>
            </section>
    
            <section v-if="filter(resume.call).length > 0">
                <h2 class="title">联系方式</h2>
                <ul>
                    <li v-for="call in filter(resume.call)">
                        <p v-if="call.phone"><span>电话</span>：{{call.phone}}</p>
                        <p v-if="call.mail"><span>邮箱</span>：{{call.mail}}</p>                   
                        <p v-if="call.qq"><span>QQ</span>：{{call.qq}}</p>
                        <p v-if="call.wechat"><span>微信</span>：{{call.wechat}}</p>
                        <p v-if="call.other">{{call.other}}</p>                    
                    </li>
                </ul>
            </section>
        </div>
    </div>
</template>


<style lang="scss">
@-webkit-keyframes leave-top{from{-webkit-transform:translate3d(0,0,0);transform:translate3d(0,0,0);z-index:0}to{-webkit-transform:translate3d(0,-100%);transform:translate3d(0,-100%);z-index:-1}}
@-moz-keyframes leave-top{from{-moz-transform:translate3d(0,0,0);transform:translate3d(0,0,0);z-index:0}to{-moz-transform:translate3d(0,-100%);transform:translate3d(0,-100%);z-index:-1}}
@keyframes leave-top{from{-webkit-transform:translate3d(0,0,0);-moz-transform:translate3d(0,0,0);transform:translate3d(0,0,0);z-index:0}to{-webkit-transform:translate3d(0,-100%,0);-moz-transform:translate3d(0,-100%,0);transform:translate3d(0,-100%,0);z-index:-1}}

@-webkit-keyframes enter-top{from{-webkit-transform:translate3d(0,-100%,0);transform:translate3d(0,-100%,0);z-index:0}to{-webkit-transform:translate3d(0,0,0);transform:translate3d(0,0,0);z-index:0}}
@-moz-keyframes enter-top{from{-moz-transform:translate3d(0,-100%,0);transform:translate3d(0,-100%,0);z-index:0}to{-moz-transform:translate3d(0,0,0);transform:translate3d(0,0,0);z-index:0}}
@keyframes enter-top{from{-webkit-transform:translate3d(0,-100%,0);-moz-transform:translate3d(0,-100%,0);transform:translate3d(0,-100%,0);z-index:0}to{-webkit-transform:translate3d(0,0,0);-moz-transform:translate3d(0,0,0);transform:translate3d(0,0,0);z-index:0}}


.leave-top {
    -webkit-animation: leave-top .5s ease-out;
    -moz-animation: leave-top .5s ease-out;
    animation: leave-top .5s ease-out;
}
.enter-top {
    -webkit-animation: enter-top .5s ease-in;
    -moz-animation: enter-top .5s ease-in;
    animation: enter-top .5s ease-in;
}

#preview{
    width: 96%;
    padding: 4%;
    position: relative;
    color: #48576A;
    .bg{
        width: 100%;
        position: absolute;
        top: 0;
        left: 0;
        z-index: -1;
        ul{
            width: 100%;
            display: flex;
            li{
                display: inline-block;
                text-align: center;
                cursor: pointer;
                line-height: 26px;
                flex:1;
                border-top: 3px solid transparent; 
                transition: border-top .6s;
                &:nth-child(1):hover,&:nth-child(1).active{
                    border-top: 3px solid #FFE5EF;
                }
                &:nth-child(2):hover,&:nth-child(2).active{
                    border-top: 3px solid #20A0FF;
                }
                &:nth-child(3):hover,&:nth-child(3).active{
                    border-top: 3px solid #FB9A00;
                }
                &:nth-child(4):hover,&:nth-child(4).active{
                    border-top: 3px solid #E0323C;
                }
                &:nth-child(5):hover,&:nth-child(5).active{
                    border-top: 3px solid #7ff9bc;
                }
                &:nth-child(6):hover,&:nth-child(6).active{
                    border-top: 3px solid #1c54f7;
                }
            }
        }   
    }
    .enter-top{
        z-index: 1;
    }
    h3{
        text-align: center;
        font-size: 22px;
        padding-bottom: 10px;
    }
    h2.title{
        font-size: 18px;
        font-weight: 400;
        display: inline-block;
        margin: 20px 0 6px -12px;
        color: #48576A;
        background: #FFE5EF;
    }
    .pink h2.title{
        background:#FFE5EF;
    }
    .sky h2.title{
        background: #20A0FF;
    }
    .orange h2.title{
        background: #FB9A00;
    }
    .red h2.title{
        background: #E0323C;
    }
    .green h2.title{
        background: #7ff9bc;
    }
    .blue h2.title{
        background: #1c54f7;
    }
    li{
        margin-bottom: 14px;
    }
    p{
        line-height: 22px;
        span{
            font-weight: 600;
        }
    }
} 
</style>

<script>
export default {
  data(){
    return{
      theme: ['pink','sky','orange','red','green','blue'],
      themeText: ['活力粉','清澈蓝','跃动橙','温莎红','喀纳斯绿','埃斯托蓝'],
      themeTab: 'pink',
      animation: ''
    }
  },
  props: ['resume'],
  methods: {
      filter(array){//遍历数组书每一个对象
            return array.filter(item=>!this.isEmpty(item))
        },
      isEmpty(obj){//如果对象中键值全为空，则返回false
        let empty = true;
        for(let key in obj){
            if(obj[key]){
                 empty = false
                 break
            }
        }
        return empty
      },
      enter(){
          this.animation = 'enter-top'
      },
      leave(){
          this.animation = 'leave-top'
      }
  },
//   computed: {
//       toHtml: function(){
//           function turn(str){
//               return ((str.replace(/<(.+?)>/gi,"&lt;$1&gt;")).replace(/ /gi,"&nbsp;")).replace(/\n/gi,"<br>")
//           }
//           console.log(this.resume)
//           return {
//               education: turn(this.resume.educationHistory.content),
//               skill: turn(this.resume.skill.list),
//               company: turn(this.resume.companyHistory.content),
//               call: turn(this.resume.call.other),
//               yourself: turn(this.resume.yourself.content)
//           }
//       }
//   }
}
</script>
