<template>
  <div>
    <div v-for="item in tagsToArr" :key="item.name" class="chosenTagsDiv">

      <button @click="deleteTag(item)">{{ item }}</button>

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
          //dodać id do każdej pracy
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
      chosenTags: [],
    }
  }
  ,
  methods: {
    displayTags(tech) {
      this.chosenTags.push(tech);

      this.jobs.map(job => {

        if (job.stack.some(el => (this.chosenTags.map(tag => tag.toLowerCase())).includes(el.toLowerCase()))) {
          job.display = true
        } else {
          job.display = false
        }
      })

    },

    deleteTag(tag) {
      this.tagsToArr = this.tagsToArr.filter(a => a != tag)
      console.log(this.tagsToArr)
    }
  },

  watch: {
    chosenTags() {
    }
  },

  computed: {
    tagsToArr: function () {
      return Array.from(new Set(this.chosenTags));
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
