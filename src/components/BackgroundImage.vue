<template>
  <div class="backgroundImage-wrapper"></div>
</template>

<script>
export default {
  name: "BackgroundImage"
};
</script>

<style lang="scss" scoped>
.backgroundImage-wrapper {
  position: fixed;
  top: 0;
  width: 100%;
  height: 100vh;
  background: url("../assets/milkyway.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  background-position: bottom center;
  z-index: -1;

  @media (min-width: 768px) {
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
  }
  @media (min-width: 1024px) {
    background-image: url("../assets/milkyway.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
  }
}
.otherBackground {
  background-image: url("../assets/background-1.png");
}
</style>>

