<template>
  <div>
    <div v-for="job in jobs" :key="job.compName">
      <Card :compName="job.compName"/>
    </div>
  </div>
</template>

<script>
import Card from './Card.vue'

export default {
  name: "Cards",
  components:
      {
        Card,
      },
  data() {
    return {
      jobs: [
        {
          compName: 'Photoshot', jobName: 'Frontend Developer', date: '1d ago', time: 'Full time', place: 'USA only',
          new: true, featured: true, stack: ['Frontend', 'Senior', 'Html', 'Css', 'JavaScript']
        },
        {
          compName: 'Manage', jobName: 'Fullstack Developer', date: '1d ago', time: 'Part Time', place: 'Remote',
          new: true, featured: true, stack: ['Fullstack', 'Midweight', 'Python', 'Eeact']
        },
        {
          compName: 'Account',
          jobName: 'Junior Frontend Developer',
          date: '2d ago',
          time: 'Part Time',
          place: 'USA only',
          new: true,
          featured: false,
          stack: ['Frontend', 'Junior', 'React', 'Sass', 'JavaScript']
        },
        {
          compName: 'MyHome', jobName: 'Junior Frontend Developer', date: '5d ago', time: 'Contract', place: 'USA only',
          new: false, featured: false, stack: ['Frontend', 'Junior', 'CSS', 'Javascript']
        },
        {
          compName: 'Loop Studios', jobName: 'Software Engineer', date: '1w ago', time: 'Full Time', place: 'Worldwide',
          new: false, featured: true, stack: ['Fullstack', 'Javascript', 'Midweight', 'Sass', 'Ruby']
        }
      ],
      nameI: 'aha'
    }
  }

}
</script>

<style scoped>

</style>
