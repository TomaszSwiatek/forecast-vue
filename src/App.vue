<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style lang="scss">
// tych styli nie scopujemy by mialy zasieg globalny. border box i ogolny reset ma byc dla wszystkich.
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,800&subset=latin-ext");
@import url("https://fonts.googleapis.com/css?family=Source+Code+Pro");
@import url("https://fonts.googleapis.com/css?family=Open+Sans+Condensed:300");
@import url("https://fonts.googleapis.com/css?family=Open+Sans");
* {
  box-sizing: border-box;
}

body {
  // font-family: "Montserrat", sans-serif;
  // font-family: "Source Code Pro", monospace;
  font-family: "Open Sans", sans-serif;
  margin: 0;
  padding: 0;
}
</style>
