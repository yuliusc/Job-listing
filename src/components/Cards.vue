<template>
  <div class="cards_container">
    <div class="tagsCont" v-show="chosenTags.length!=0">
      <div class="chosenTagsDiv">
        <div v-for="item in chosenTags" :key="item.name" class="chosenTag">
          <span>{{ item }}</span>
          <button @click="deleteTag(item)" class="chosenTag__delete">
            <img src="../../public/images/icon-remove.svg" class="chosenTag__icon">
          </button>
        </div>
      </div>
      <div class="chosenTagsDiv__clear_div">
        <button @click="clearTags()" class="chosenTagsDiv__clear">Clear</button>
      </div>
    </div>
    <div class="break"></div>
    <div class="break2" v-show="chosenTags.length!=0"></div>
    <div v-for="job in jobs" :key="job.compName">
      <Card :compName="job.compName" :jobName="job.jobName" :date="job.date"
            :time="job.time" :place="job.place" :newO="job.newO"
            :featured="job.featured" :stack="job.stack" :class="{displayN: !job.display}"
            @displayTags="displayTags" :imgSrc="job.imgSrc"/>
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
          compName: 'Photoshot',
          jobName: 'Frontend Developer',
          date: '1d ago',
          time: 'Full time',
          place: 'USA only',
          newO: true,
          featured: true,
          stack: ['Frontend', 'Senior', 'Html', 'Css', 'JavaScript'],
          display: true,
          imgSrc: 'photosnap.svg'
        },
        {
          compName: 'Manage',
          jobName: 'Fullstack Developer',
          date: '1d ago',
          time: 'Part Time',
          place: 'Remote',
          newO: true,
          featured: true,
          stack: ['Fullstack', 'Midweight', 'Python', 'React'],
          display: true,
          imgSrc: 'manage.svg'
        },
        {
          compName: 'Account',
          jobName: 'Junior Frontend Developer',
          date: '2d ago',
          time: 'Part Time',
          place: 'USA only',
          newO: true,
          featured: false,
          stack: ['Frontend', 'Junior', 'React', 'Sass', 'JavaScript'], display: true, imgSrc: 'account.svg'
        },
        {
          compName: 'MyHome',
          jobName: 'Junior Frontend Developer',
          date: '5d ago',
          time: 'Contract',
          place: 'USA only',
          newO: false,
          featured: false,
          stack: ['Frontend', 'Junior', 'CSS', 'Javascript'],
          display: true,
          imgSrc: 'myhome.svg'
        },
        {
          compName: 'Loop Studios',
          jobName: 'Software Engineer',
          date: '1w ago',
          time: 'Full Time',
          place: 'Worldwide',
          newO: false,
          featured: false,
          stack: ['Fullstack', 'Javascript', 'Midweight', 'Sass', 'Ruby'],
          display: true,
          imgSrc: 'loop-studios.svg'
        },
        {
          compName: 'FaceIt', jobName: 'Junior Backend Developer', date: '2w ago', time: 'Full Time', place: 'UK only',
          newO: false, featured: false, stack: ['Backend', 'Junior', 'Rub', 'RoR'], display: true, imgSrc: 'faceit.svg'
        },
        {
          compName: 'Shortly',
          jobName: 'Junior Developer',
          date: '2w ago',
          time: 'Full Time',
          place: 'Worldwide',
          newO: false,
          featured: false,
          stack: ['Frontend', 'Junior', 'HTLM', 'Sass', 'JavaScript'],
          display: true,
          imgSrc: 'shortly.svg'
        },
        {
          compName: 'Insure',
          jobName: 'Junior Frontend Developer',
          date: '2w ago',
          time: 'Full Time',
          place: 'USA olny',
          newO: false,
          featured: false,
          stack: ['Frontend', 'Junior', 'Vue', 'Sass', 'JavaScript'],
          display: true,
          imgSrc: 'insure.svg'
        },
        {
          compName: 'EyeCam Co.',
          jobName: 'Full Stack Engineer',
          date: '3w ago',
          time: 'Full Time',
          place: 'Worldwide',
          newO: false,
          featured: false,
          stack: ['Fullstack', 'Midweight', 'Django', 'Python', 'JavaScript'],
          display: true,
          imgSrc: 'eyecam-co.svg'
        },
        {
          compName: 'The Air Filter Company',
          jobName: 'Front-end Dev',
          date: '1mo ago',
          time: 'Part Time',
          place: 'Worldwide',
          newO: false,
          featured: false,
          stack: ['Frontend', 'React', 'Sass', 'Junior', 'JavaScript'],
          display: true,
          imgSrc: 'the-air-filter-company.svg'
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

          let lowerCT = this.chosenTags.map(tag => tag.toLowerCase())
          let lowerJS = job.stack.map(j => j.toLowerCase())

          if (lowerCT.every(el => lowerJS.includes(el))) {
            job.display = true
          } else {
            job.display = false;
          }
        })
      } else {
        this.jobs.map(el => el.display = true)
      }

    },

    deleteTag(tag) {
      this.chosenTags = this.chosenTags.filter(a => a != tag)
      this.updateDisplay();
    },

    clearTags() {
      this.chosenTags = [];
      this.updateDisplay();
    }
  },


}
</script>

<style scoped>
@import "../styles/cards.css";

.displayN {
  display: none;
}

.display {
  display: flex !important;
}


</style>
