<template>
  <div class="search-wrapper">
    <!-- tutaj bindujemy wartosc inputa do propsa - tak trzeba. robimy propsa wew. scriptowych bebechow komponentu, nastepnie dajemy event do ktorego przypisujemy funkcje ktora wyemituje nazewnattz wartosc value -->
    <input id="search" name="search" :value="value" @input="handleChange">
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
  name: "Search",
  props: {
    value: {
      type: String,
      required: true
    }
  },
  methods: {
    handleChange(e) {
      this.$emit("input", e.target.value);
    }
  }
};
</script>

<style lang="scss" scoped>
.search-wrapper {
  margin-top: 3rem;
  display: flex;
  flex-direction: column;
  width: 50vw;
}
input {
  // height: 30px;
  border: 0;
  border-bottom: 1px solid white;
  background-color: transparent;
  color: white;
  transition: box-shadow linear 0.5s;
  font-size: 1.3rem;
  font-family: "Open Sans", sans-serif;
  text-transform: uppercase;
  text-align: center;
  &:focus {
    outline: none; //nie robi sie kwadrat na focusie
    box-shadow: 0px 10px 20px -8px rgba(255, 255, 255, 0.5);
  }
}
@media (min-width: 768px) {
  input {
    font-size: 2.5rem;
  }
}
</style>>

