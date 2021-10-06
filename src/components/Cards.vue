<template>
  <div class="cards_container">
    <div class="chosenTagsDiv">
      <div v-for="item in chosenTags" :key="item.name" class="chosenTag">
        <span>{{ item }}</span><button @click="deleteTag(item)">X</button>
      </div>
    </div>
    <div class="break"></div>
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
          //dodać id do każdej pracy
          compName: 'Photoshot', jobName: 'Frontend Developer', date: '1d ago', time: 'Full time', place: 'USA only',
          newO: true, featured: true, stack: ['Frontend', 'Senior', 'Html', 'Css', 'JavaScript'], display: true
        },
        {
          compName: 'Manage', jobName: 'Fullstack Developer', date: '1d ago', time: 'Part Time', place: 'Remote',
          newO: true, featured: true, stack: ['Fullstack', 'Midweight', 'Python', 'React'], display: true
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
        },
        {
          compName: 'FaceIt', jobName: 'Junior Backend Developer', date: '2w ago', time: 'Full Time', place: 'UK only',
          newO: false, featured: false, stack: ['Backend', 'Junior', 'Rub', 'RoR'], display: true
        },
        {
          compName: 'Shortly', jobName: 'Junior Developer', date: '2w ago', time: 'Full Time', place: 'Worldwide',
          newO: false, featured: false, stack: ['Frontend', 'Junior', 'HTLM', 'Sass', 'JavaScript'], display: true
        },
        {
          compName: 'Insecure', jobName: 'Junior Frontend Developer', date: '2w ago', time: 'Full Time', place: 'USA olny',
          newO: false, featured: false, stack: ['Frontend', 'Junior', 'Vue', 'Sass', 'JavaScript'], display: true
        },
        {
          compName: 'EyeCam Co.', jobName: 'Full Stack Engineer', date: '3w ago', time: 'Full Time', place: 'Worldwide',
          newO: false, featured: false, stack: ['Fullstack', 'Midweight', 'Django', 'Python', 'JavaScript'], display: true
        },
        {
          compName: 'The Air Filter Company', jobName: 'Front-end Dev', date: '1mo ago', time: 'Part Time', place: 'Worldwide',
          newO: false, featured: false, stack: ['Frontend', 'React', 'Sass', 'Junior', 'JavaScript'], display: true
        },
      ],
      chosenTags: [],
    }
  }
  ,
  methods: {
    displayTags(tech) {
      if (!this.chosenTags.includes(tech))
        this.chosenTags.push(tech);

      this.updateDisplay();

    },

    updateDisplay() {
      if (this.chosenTags.length != 0) {
        this.jobs.map(job => {

          if (job.stack.some(el => (this.chosenTags.map(tag => tag.toLowerCase())).includes(el.toLowerCase()))) {
            job.display = true
          } else {
            job.display = false
          }
        })
      } else {
        this.jobs.map(el => el.display = true)
      }

    },

    deleteTag(tag) {
      this.chosenTags = this.chosenTags.filter(a => a != tag)
      this.updateDisplay();
    }
  },


}
</script>

<style scoped>

.displayN {
  display: none;
}

.display {
  display: flex !important;
}

.cards_container{
  width: 80%;
  display: flex;
  flex-direction: column;
  margin: 0 auto;
}

.chosenTagsDiv{
  background: white;
  height: 74px;
  margin-top: -37px;
  display: flex;
  align-items: center;
  border-radius: 0.5rem;
}

</style>
