<template>
    <div id="preview" class="scroll">
        <section v-if="!isEmpty(resume.profile)">
            <h3>{{resume.profile.name}}</h3>
            <p>{{resume.profile.sex}}</p>
            <p>{{resume.profile.city}}</p>
            <p>{{resume.profile.birth}}</p>
        </section>
        <section v-if="filter(resume.companyHistory).length > 0">
            <ul>
                <li v-for="companyHistory in filter(resume.companyHistory)">
                    <p>{{companyHistory.company}}</p>
                    <p>{{companyHistory.time}}</p>
                    <p>{{companyHistory.job}}</p>
                    <p>{{companyHistory.content}}</p>
                </li>
            </ul>
        </section>
        <section v-if="filter(resume.educationHistory).length > 0">
            <ul>
                <li v-for="educationHistory in filter(resume.educationHistory)">
                    <p>{{educationHistory.school}}</p>
                    <p>{{educationHistory.duration}}</p>
                    <p>{{educationHistory.degree}}</p>
                    <p>{{educationHistory.major}}</p>                    
                    <p>{{educationHistory.content}}</p>
                </li>
            </ul>
        </section>

        <section v-if="!isEmpty(resume.yourself)">
            <p>{{resume.yourself.content}}</p>
        </section>

        <section v-if="filter(resume.skill).length > 0">
            <ul>
                <li v-for="skill in filter(resume.skill)">
                    <p>{{skill.list}}</p>
                </li>
            </ul>
        </section>

        <section v-if="filter(resume.project).length > 0">
            <ul>
                <li v-for="project in filter(resume.project)">
                    <p>{{project.name}}</p>
                    <p>{{project.time}}</p>                   
                    <p>{{project.content}}</p>
                </li>
            </ul>
        </section>

        <section v-if="filter(resume.call).length > 0">
            <ul>
                <li v-for="call in filter(resume.call)">
                    <p>{{call.phone}}</p>
                    <p>{{call.mail}}</p>                   
                    <p>{{call.qq}}</p>
                    <p>{{call.other}}</p>                    
                </li>
            </ul>
        </section>
    </div>
</template>


<style>
#preview{
    width: 96%;
    padding: 10px;
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
