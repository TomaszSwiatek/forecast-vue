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
@mixin transparentBg {
  background: hsla(0, 71%, 3%, 0.3);
  overflow: hidden;
  border-radius: 10px;
}
.claim-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: center;
  text-align: center;
  color: white;
  padding: 1rem;
  //blur in background
  @include transparentBg;
  margin: 0 1rem;
  h1 {
    text-transform: uppercase;
    font-size: 3rem;
    margin: 0;
  }
  p {
    margin-top: 1.2rem;
    font-size: 1rem;
  }
  @media (min-width: 768px) {
    margin: 0 6rem;
    h1 {
      font-size: 7rem;
    }
    p {
      font-size: 1.7rem;
      margin: 5% 10%;
      font-weight: 100;
      letter-spacing: 0.5rem; //odstep miedzy znakami
      line-height: 1.5; //odstep miedzy wierszami
    }
  }
  @media (min-width: 1024px) {
    margin: 0 25%;
    h1 {
      font-size: 9rem;
      margin: 2% 0 7% 0;
    }
    p {
      font-size: 1.7rem;
      margin: 1% 15%;
      font-weight: 100;
      letter-spacing: 0.5rem; //odstep miedzy znakami
      line-height: 1.5; //odstep miedzy wierszami
    }
  }
}
</style>>

