<template lang="pug">
  #app
    h1 todos app
    hr
    router-view
</template>

<style lang="scss">
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin: 60px auto;
    max-width: 600px;
  }

  hr {
    width: 100%;
    height: 1px;
    border: 0;
    background: #e3e3e3;
  }

  // vars colors

  // $gray: #2c3e50;
  // $green: #4fc08d;
  // $gray: #e3e3e3;
  // $gray-dark: #2c3e50;

</style>
