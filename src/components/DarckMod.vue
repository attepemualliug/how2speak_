<template>
    <div class="switcher">
      <h1 class="switcher__title">{{ title }}</h1>
      <b-form-checkbox
        class="switcher__checkbox"
        name="switcher"
        @change="changeThemeColor"
        switch
        v-model="checked"
      >
        <p v-if="checked">Dark-Theme</p>
        <p v-else>Light-Theme</p>
      </b-form-checkbox>
    </div>
  </template>
  
  <script>
  export default {
    name: "DarckMod",
    props: {
      title: {
        type: String,
        required: false,
        default: "Translate your sentence :)"
      }
    },
    data() {
      return {
        checked: true
      };
    },
    methods: {
      changeThemeColor() {
        const appWrapper = document.getElementById("app-wrapper");
        const currentClass = appWrapper.className;
        appWrapper.className =
          currentClass == "dark-mode" ? "light-mode" : "dark-mode";
      }
    }
  };
  </script>
  
  <style lang="scss">
  .switcher {
    &__title {
      margin: 20px 0;
    }
    &__checkbox {
      display: inline-block;
      label {
        &:hover {
          cursor: pointer;
        }
      }
    }
  }
  </style>
  