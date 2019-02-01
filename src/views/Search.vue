<template>
  <div class="wrapper">
    <Claim/>
    <Search/>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";
import debounce from "lodash.debounce";
const API = "https://api.openweathermap.org/data/2.5/forecast?q=";
const API_ID = "&appid=8516c35a5aa25a2690f4dca7c0d11239";
import Claim from "@/components/Claim.vue";
import Search from "@/components/Search.vue";

export default {
  name: "search",
  components: { Claim, Search },
  //data w komponencie musi byc funkcja ktora zwraca obiekt, nie moze byc czystym obiektem
  data() {
    return {
      searchValue: "" //jezeli deklarujemy v-model, to zmienna na ktorej operujemy musi miec inicjalna wartosc, inaczej zmienna przypisana do vmodel w input nie bedzie reaktywna
      // results: [] //zmienna w ktorej przechowamy dane
    };
  },
  methods: {
    handleInput: debounce(function() {
      //koniecznie normalna fcja anonimowa. by zrobic fcje w funkcji przypisujemy klucz eventu i w jej parametrze funkcje z funkcja anonimowa w srodku - wynika to z dokumentacji lodasha. za funkcją po przecinku dajemy zwłokę którą czeka funkcja by nie wysyłała niepotrzebnych requestów.
      axios
        .get(`${API}${this.searchValue}${API_ID}`)
        .then(response => {
          console.log(response.data.list);
          this.results = response.data.list;
        })
        .catch(error => {
          //w przeciwnym razie jezeli nie wyswietli odpowiedzi (to co wyzej), to wyswietl bledy
          console.log(`erorrrrr: ${error}`);
        });
    }, 500)
    // console.log(e.target.value); //cos takiego loguje to co wpiszemy na bierzaco do konsoli
    // console.log(this.searchValue); //drugi sposób
  }
};
</script>
<style lang="scss" scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin: 0;
  padding: 2rem;
  width: 100%;
  min-height: 100vh;

  width: 100%;
  margin: 0;
  // padding: 30px;

  background-image: url("../assets/widok-okno-ofc-wschod-piatkowo.jpg");
  background-size: cover;
}
</style>

