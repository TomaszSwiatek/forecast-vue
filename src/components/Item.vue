<template>
  <div class="wrapper-item">
    <div class="item">
      <p>{{toCelcius(temp)}}</p>
      <p>{{`today at least temperature ${toCelcius(tempMin)}`}}</p>
      <p>{{`today maximum temperature ${toCelcius(tempMax)}`}}</p>
      <p>{{`at this time you can expect ${description}`}}</p>
      <p>{{`img icon number ${iconId}`}}</p>
      <p>{{`Humidity is ${humidity}`}}</p>
      <p>{{`Pressure is ${pressure}`}}</p>
      <p>{{`Wind's speed circa ${speed}`}}</p>
      <p>{{`Wind's direction ${deg}`}}</p>
      <p>{{date}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Item",
  props: {
    item: {
      type: String, //? Object
      required: true
    }
  },
  data() {
    return {
      temp: this.item.main.temp,
      tempMin: this.item.main.temp_min,
      tempMax: this.item.main.temp_max,
      description: this.item.weather[0].description,
      iconId: this.item.weather[0].icon,
      humudity: this.item.main.humidity,
      pressure: this.item.main.pressure,
      speed: this.item.wind.speed,
      windDirection: this.item.wind.deg,
      date: this.item.dt_txt
    };
  },
  methods: {
    toCelcius(kelvin) {
      return `${Math.floor(kelvin - 273.15)}`;
    },
    filterByDate() {
      return this.$options.filters.item.date;
    }
  }
  //   computed: {
  //     temp() {
  //       return this.item.main.temp;
  //     }
  //   }
  //   mounted() {
  //     this.temp = this.item.main.temp;
  //   }
};
</script>

<style lang="scss" scoped>
.wrapper-item {
  .item {
    margin: 2rem;
  }
}
</style>

