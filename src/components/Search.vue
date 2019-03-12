<template>
  <div class="search-wrapper">
    <!-- w skrócie dark: dark wg es6 mozemy zapisac dark, a jest to w sumie przypisanie propsa do faktycznej klasy css o nazwie dark -->
    <input id="search" name="search" :class="{dark : dark}" :value="value" @input="handleChange">
    <!--  <ul>
        jak juz spakowalismy dane do tablicy to ją wyświetlimy przy pomocy dyrektywy v-for
        <li v-for="item in results" :key="item.dt">
          <p>{{ item.main.temp }}</p>
        </li>
    </ul>-->
  </div>
</template>

<script>
export default {
  name: 'Search',
  props: {
    value: {
      type: String,
      required: true,
    },
    // tutaj wstawiamy propsa który akurat bedzie uzyty w app.vue ale w componencie tego pliku. natomiast props value odnosi sie do imputa który składa sie na ten komponent ( w tym pliku)
    dark: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    handleChange(e) {
      this.$emit('input', e.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
$dark-color: #1e3d4a;
@mixin transparentBg {
  background: hsla(0, 71%, 3%, 0.3);
  overflow: hidden;
  border-radius: 7px;
  padding: 1rem;
}
.search-wrapper {
  margin-top: 3rem;
  display: flex;
  flex-direction: column;
  width: 50vw;
}
input {
  @include transparentBg;
  border: 0;
  border-bottom: 1px solid white;
  // background-color: transparent;
  color: white;
  transition: box-shadow linear 0.5s;
  font-size: 1.3rem;
  font-family: "Open Sans", sans-serif;
  text-transform: uppercase;
  text-align: center;
  &:focus {
    outline: none; //nie robi sie kwadrat na focusie
    box-shadow: 0px 12px 10px -10px rgba(255, 255, 255, 0.5);
  }
  //   class bind to props: dark - turn on when dark is true. dark === true when step === 1, so in second app view. See - search component in app.vue and an input tag inside component.
  &.dark {
    color: $dark-color;
    border-bottom-color: $dark-color;
    &:focus {
      box-shadow: 0px 12px 10px -10px rgba($dark-color, 0.5);
    }
  }
}

@media (min-width: 768px) {
  input {
    font-size: 2.5rem;
  }
}
</style>

