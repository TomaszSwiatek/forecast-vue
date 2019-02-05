<template>
  <!-- jedna klasa nadana warunkowo, druga zwykla. w takim przypadku musimy wszystko oplesc w tabele by dzialalo. musimy tez zbindowac tag class. ( dlaczego?) -->
  <div :class="[{flexStart: step === 1 }, 'wrapper']">
    <transition name="slide">
      <img src="./assets/3.svg" v-if="step === 1" class="logo">
    </transition>

    <transition name="fade">
      <BackgroundImage v-if="step === 0"/>
    </transition>

    <Claim v-if="step === 0"/>
    <Search v-model="searchValue" @input="handleInput" :dark="step === 1"/>
    <div class="results" v-if="results && !loading && step === 1">
      <Item v-for="item in results" :item="item" :key="item.dt"/>
      <!-- <div v-for="item in results" :key="item.dt">
       <p>{{item.main.temp}}</p>
        <p>{{`today at least temperature ${item.main.temp_min}`}}</p>
        <p>{{`today maximum temperature ${item.main.temp_max}`}}</p>
        <p>{{`at this time you can expect ${item.weather[0].description}`}}</p>
        <p>{{`img icon number ${item.weather[0].icon}`}}</p>
        <p>{{`Humidity is ${item.main.humidity}`}}</p>
        <p>{{`Pressure is ${item.main.pressure}`}}</p>
        <p>{{`Wind's speed circa ${item.wind.speed}`}}</p>
        <p>{{`Wind's direction  ${item.wind.deg}`}}</p>
        <p>{{item.dt_txt}}</p>
      </div>-->
    </div>
  </div>
</template>




<script>
import axios from "axios";
import debounce from "lodash.debounce";
const API = "https://api.openweathermap.org/data/2.5/forecast?q=";
const API_ID = "&appid=8516c35a5aa25a2690f4dca7c0d11239";
import Claim from "@/components/Claim.vue";
import Search from "@/components/Search.vue";
import BackgroundImage from "@/components/BackgroundImage.vue";
import Item from "@/components/Item.vue";

export default {
  name: "App",
  components: { Claim, Search, BackgroundImage, Item },
  data() {
    return {
      loading: false,
      step: 0, //stan poczatkowy - zmieniamy state i potem za pomocoa v-if pokazujemuy w tagu html co ma byc widoczne w danym stanie. mozemy do tego dodać stransition jako tag i wystylowac przejscie w css. liczy sie name tag. wiecej vue-transition
      searchValue: "",
      results: [] //zmienna w ktorej przechowamy dane
    };
  },
  methods: {
    handleInput: debounce(function() {
      this.loading = true; //when interpreter is exactly here loading turn to true.
      // console.log(this.searchValue);
      axios
        .get(`${API}${this.searchValue}${API_ID}`)
        .then(response => {
          console.log(response.data.list);
          this.results = response.data.list;
          this.loading = false; //after this line loading again is false. we do it to manage states in tags with v-if directive.
          this.step = 1; //after this line we change to second state.
        })
        .catch(error => {
          console.log(`erorrrrr: ${error}`);
        });
    }, 500)
  }
};
</script>

<style lang="scss">
// tych styli nie scopujemy by mialy zasieg globalny. border box i ogolny reset ma byc dla wszystkich.
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,800&subset=latin-ext");
@import url("https://fonts.googleapis.com/css?family=Source+Code+Pro");
@import url("https://fonts.googleapis.com/css?family=Open+Sans+Condensed:300");
@import url("https://fonts.googleapis.com/css?family=Open+Sans");
* {
  box-sizing: border-box;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  font-family: "Open Sans", sans-serif;
  margin: 0;
  padding: 0;

  //to style transition we have 4 states - see vue docs- there is an img. (v-enter; v-enter-to (this two states are v-enter-active))(v-leave ; v-leave-to (and these v-leave-active))
  //here are at all 4 classes
  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 0.9s ease;
  }
  //here we overwrite 2 of 4 classes - the first and the last one.
  .fade-enter,
  .fade-leave-to {
    opacity: 0;
  }
  //____________________________________________
  .slide-enter-active,
  .slide-leave-active {
    transition: margin-top 0.9s ease;
  }
  //here we overwrite 2 of 4 classes - the first and the last one.
  .slide-enter,
  .slide-leave-to {
    margin-top: -50px;
  }
  .wrapper {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    margin: 0;

    width: 100%;
    min-height: 100vh;
    width: 100%;
    padding-top: 10vh;

    //adds this class to wrapper when step === 1 - see wrapper tag.
    &.flexStart {
      justify-content: flex-start;
    }
  }
  .logo {
    position: absolute;
    top: 4vh; //padding is in vh, we ll try to config all by vh  to do our absolute element responsive
    height: 6vh;
  }
} //end of body
</style>
