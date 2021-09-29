<template>
  <div>
    <div class="chosenTagsDiv">

      {{this.chosenTags}}

    </div>
    <div v-for="job in jobs" :key="job.compName">
      <Card :compName="job.compName" :jobName="job.jobName" :date="job.date"
            :time="job.time" :place="job.place" :newO="job.newO"
            :featured="job.featured" :stack="job.stack" :class="{displayN: !job.display}"
            @displayTags="displayTags"/>
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
          newO: true, featured: true, stack: ['Frontend', 'Senior', 'Html', 'Css', 'JavaScript'], display: true
        },
        {
          compName: 'Manage', jobName: 'Fullstack Developer', date: '1d ago', time: 'Part Time', place: 'Remote',
          newO: true, featured: true, stack: ['Fullstack', 'Midweight', 'Python', 'Eeact'], display: true
        },
        {
          compName: 'Account',
          jobName: 'Junior Frontend Developer',
          date: '2d ago',
          time: 'Part Time',
          place: 'USA only',
          newO: true,
          featured: false,
          stack: ['Frontend', 'Junior', 'React', 'Sass', 'JavaScript'], display: true
        },
        {
          compName: 'MyHome', jobName: 'Junior Frontend Developer', date: '5d ago', time: 'Contract', place: 'USA only',
          newO: false, featured: false, stack: ['Frontend', 'Junior', 'CSS', 'Javascript'], display: true
        },
        {
          compName: 'Loop Studios', jobName: 'Software Engineer', date: '1w ago', time: 'Full Time', place: 'Worldwide',
          newO: false, featured: false, stack: ['Fullstack', 'Javascript', 'Midweight', 'Sass', 'Ruby'], display: true
        }
      ],
      nameI: 'aha',
      chosenTags: [],
    }
  }
  ,
  methods: {
    displayTags(tech) {
      this.chosenTags.push(tech);
      this.jobs.map(el => {

        if (el.stack.some(r => this.chosenTags.includes(r))) {
          el.display = true
        } else {
          el.display = false
        }
      })
    }
  },

  watch: {
    chosenTags() {
      console.log('zmiana')
    }
  }

}
</script>

<style scoped>

.displayN {
  display: none;
}

.display {
  display: flex !important;
}

</style>
