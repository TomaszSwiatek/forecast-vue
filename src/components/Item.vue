<template>
  <div class="wrapper-item">
    <span>{{date}}</span>
    <span class="description">{{`${description}`}}</span>
    <header>
      <img :src="src" :alt="description">
      <div class="temp">
        <span>{{`${toCelcius(temp)} °C`}}</span>
        <span>{{`At least ${toCelcius(tempMin)} °C`}}</span>
        <span>{{`The most ${toCelcius(tempMax)} °C`}}</span>
      </div>
    </header>
    <main>
      <span>{{`Humidity:${humidity}`}}</span>
      <span>{{`Pressure:${Math.floor(pressure)} hPa`}}</span>
      <span>{{`Wind's speed: ${Math.floor(speed)} mph`}}</span>
      <span>{{`Wind's direction: ${Math.floor(windDirection)}`}}</span>
    </main>
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
      humidity: this.item.main.humidity,
      pressure: this.item.main.pressure,
      speed: this.item.wind.speed,
      windDirection: this.item.wind.deg,
      date: this.item.dt_txt,
      ApiImageLink: "http://openweathermap.org/img/w/"
    };
  },
  computed: {
    src() {
      return `${this.ApiImageLink}${this.iconId}.png`;
    }
  },
  methods: {
    toCelcius(kelvin) {
      return `${Math.floor(kelvin - 273.15)}`;
    },
    windsDirection(angle) {
      angle;
    }
    // filterByDate(day) {
    //   return this.$options.filters.item.date(day);
    // }
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
  font-family: "Open Sans", sans-serif;
  //   color: white;
  //   border-bottom: 1px solid black;
  display: flex;
  flex-direction: column;
  margin: 1.5rem 1rem;
  padding: 0.5rem;
  text-align: center;
  background: #fff;
  //   border-radius: 10px;

  //   background-color: rgba(9, 114, 159, 0.8);
  //   border: 1px solid rgb(9, 114, 159);
  .description {
    margin: 1rem 0;
    font-size: 1.8rem;
  }
}
img {
  width: 30%;
}
header {
  display: flex;
  margin: 0.5rem;
  align-items: center;
  justify-content: space-evenly; //nie dziala kiedy ustawisz na rodzicu align items na center, lub cokolwiek
  .temp {
    display: flex;
    flex-direction: column;
    align-items: start;
  }
}
main {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  padding-top: 1rem;
}
span {
  display: inline-block;
  margin: 0;
  padding: 0;
  padding-right: 0.6rem;
}
</style>

