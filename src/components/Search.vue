<template>
  <div class="search-wrapper">
    <div class="search">
      <!-- <label for="search">Search</label> -->
      <input id="search" name="search" v-model="searchValue" @input="handleInput">
      <!--  <ul>
        jak juz spakowalismy dane do tablicy to ją wyświetlimy przy pomocy dyrektywy v-for 
        <li v-for="item in results" :key="item.dt">
          <p>{{ item.main.temp }}</p>
        </li> 
      </ul>-->
    </div>
  </div>
</template>

<script>
export default {
  name: "Search"
};
</script>

<style lang="scss" scoped>
.search-wrapper {
  .search {
    margin-top: 3rem;
    display: flex;
    flex-direction: column;
    width: 250px;
  }
  input {
    height: 30px;
    border: 0;
    border-bottom: 1px solid white;
    background-color: transparent;
  }
  label {
    font-family: Montserrat, sans-serif;
    color: white;
  }
}
</style>>

