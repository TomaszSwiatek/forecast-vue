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
  background-image: url("../assets/check-weather-1.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  background-position: 10% 0%;
  z-index: -1;
  &::after {
    content: "";
    background: rgba($color: #2f2100, $alpha: 0.2);
    position: absolute;
    top: 0;
    left: 0;
    z-index: 1;
    width: 100%;
    height: 100vh;
  }
  @media (min-width: 768px) {
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
  }
  @media (min-width: 1024px) {
    background-image: url("../assets/check-weather-1-desktop.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
  }
}
</style>>

