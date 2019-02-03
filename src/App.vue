<template>
  <div class="wrapper">
    <BackgroundImage v-if="step === 0"/>
    <Claim v-if="step === 0"/>
    <Search v-model="searchValue" @input="handleInput" :dark="step === 1"/>
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

export default {
  name: "App",
  components: { Claim, Search, BackgroundImage },
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

  .wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin: 0;

    width: 100%;
    min-height: 100vh;
    width: 100%;
    padding: 0 2rem;
  }
}
</style>
