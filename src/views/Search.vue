<template>
  <div class="wrapper">
    <div class="search">
      <label for="search">Search</label>
      <input type="text" id="search" name="search">
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue';

export default {
  name: "search"
};
</script>
<style lang="scss" scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;

  width: 100%;
  margin: 0;
  padding: 30px;
  .search {
    display: flex;
    flex-direction: column;
    width: 250px;
  }
  input {
    height: 30px;
    border: 0;
    border-bottom: 1px solid black;
  }
  label {
    font-family: Montserrat, sans-serif;
  }
}
</style>

