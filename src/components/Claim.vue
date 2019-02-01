<template>
  <div class="claim-wrapper">
    <h1 class="claim">Weather</h1>
    <p
      class="sub-claim"
    >Check the weather in your city. You can also see what the current weather is at the place you want to go to.</p>
    <p class="sub-claim">Browse the five-day weather for a selected place on the earth!</p>
  </div>
</template>

<script>
export default {
  name: "Claim"
};
</script>

<style lang="scss" scoped>
.claim-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: center;
  text-align: center;
  // font-family: "Montserrat", sans-serif;
  color: white;
  h1 {
    text-transform: uppercase;
    font-size: 3rem;
    margin: 0;
  }
  p {
    margin-top: 1.2rem;
    font-size: 0.8rem;
  }
}
</style>>

