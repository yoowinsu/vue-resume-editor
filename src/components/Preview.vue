<template>
    <div id="preview" class="scroll">

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
                    <p v-if="companyHistory.timeStart"><span>在职时间</span>：{{companyHistory.timeStart}}————{{companyHistory.timeEnd}}</p>
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
                    <p v-if="educationHistory.duration"><span>时间</span>：{{educationHistory.duration}}</p>
                    <p v-if="educationHistory.degree"><span>学位</span>：{{educationHistory.degree}}</p>
                    <p v-if="educationHistory.major"><span>专业</span>：{{educationHistory.major}}</p>                    
                    <p v-if="educationHistory.content"><span>奖项</span>：{{educationHistory.content}}</p>
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
                    <p v-if="project.time"><span>时间</span>：{{project.time}}</p>                   
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
                    <p v-if="call.other">{{call.other}}</p>                    
                </li>
            </ul>
        </section>
    </div>
</template>


<style lang="scss">
#preview{
    width: 96%;
    padding: 4%;
    h2.title{
        font-size: 18px;
        font-weight: 400;
        margin: 20px 0 6px -12px;
        background: linear-gradient(to right, #FFE5EF, #fff);
    }
    li{
            margin-bottom: 14px;
    }
    p{
        line-height: 22px;
        span{
            font-weight: 500;
        }
    }
} 
</style>

<script>
export default {
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
      }
  }
}
</script>
