<template>

  <div class="card">

    <div class="cardPhoto">
      <img src="../../public/images/photosnap.svg">
    </div>

    <div class="cardInfo">

      <div class="cardCompName">
        <p class="cardCompName__name">{{compName}}</p>
        <ul class="cardCompName__tags">
          <li class="cardCompName__tags cardCompName__tags--new">NEW</li>
          <li class="cardCompName__tags cardCompName__tags--featured">FEATURED</li>
        </ul>
      </div>

      <div class="cardPosition">
        <h2 class="cardPosition__name">Junior Frontend Developer</h2>
      </div>

      <div class="cardDetails">
        <p class="cardDetails__date">1 day ago</p>
        <p class="cardDetails__dot">o</p>
        <p class="cardDetails__time"> Full Time </p>
        <p class="cardDetails__dot">o</p>
        <p class="cardDetails__city"> Amsterdam </p>

      </div>

    </div>

    <div class="cardStack">
      <ul class="cardStack__elements">
        <li>HTML</li>
        <li>JS</li>
        <li>SCSS</li>
        <li>VUE</li>
      </ul>
    </div>

  </div>

</template>

<script>
export default {
  name: "Card",
  props:{
    compName: String,
  },
}
</script>

<style>
@import "../styles/card.css";
</style>
