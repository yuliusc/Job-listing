<template>

  <div class="card">

    <div class="cardPhoto">
      <img src="../../public/images/photosnap.svg">
    </div>

    <div class="cardInfo">

      <div class="cardCompName">
        <p class="cardCompName__name">{{compName}}</p>
        <ul class="cardCompName__tags">
          <li class="cardCompName__tags cardCompName__tags--new" v-if="newO === true">NEW</li>
          <li class="cardCompName__tags cardCompName__tags--featured" v-if="featured === true">FEATURED</li>
        </ul>
      </div>

      <div class="cardPosition">
        <h2 class="cardPosition__name">{{jobName}}</h2>
      </div>

      <div class="cardDetails">
        <p class="cardDetails__date">{{date}}</p>
        <p class="cardDetails__dot">o</p>
        <p class="cardDetails__time"> {{time}} </p>
        <p class="cardDetails__dot">o</p>
        <p class="cardDetails__city"> {{place}} </p>

      </div>

    </div>

    <div class="cardStack">
      <ul class="cardStack__elements" v-for="tech in stack" :key="tech.compName">
        <button @click="$emit('displayTags',tech)"> <li>{{tech}}</li></button>
      </ul>
    </div>

  </div>

</template>

<script>
export default {
  name: "Card",
  props:{
    compName: String,
    jobName: String,
    date:String,
    time:String,
    place: String,
    newO: Boolean,
    featured: Boolean,
    stack: Array
  },

  emits:['displayTags'],
}
</script>

<style>
@import "../styles/card.css";
</style>
