<template>
    <div class="Switcher">

        <b-spinner 
        variant="success" 
        type="grow" 
        label="Spinning">

        </b-spinner>
    </div>
  </template>
  
  <script>
  export default {
    name: "SwitcherTranslation"
  };
  </script>
  
  <style lang="scss" scoped>
  .Switcher {
    margin-top: 30%;
      height: 6rem;
      width: 6rem;
    @media only screen and (max-width: 750px) {
      .Switcher {
        margin-top: 50%;
      }
    }
  }
  </style>
  