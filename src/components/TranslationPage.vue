<template>
  <b-container class="bv-example-row">
    <SwitcherTranslation v-if="loading" />
    <div v-else>
      <DarckMod />
      <LangSelector
        @onLangFromSelect="updatePairFrom"
        @onLangToSelect="updatePairTo"
      ></LangSelector>
      <b-row>
        <b-col class=" mb-3" lg="6" md="6" sm="12">
          <b-form-textarea
            class="textarea w-100"
            type="text"
            rows="9"
            v-model="inputValue"
            :placeholder="placeholder"
            @keyup="translate"
            aria-label="Original text to be translated"
          >
          </b-form-textarea>
          <div v-show="this.inputValue">
            <DelButton
              @deleteText="deleteTextValue"
            />
          </div>
        </b-col>

        <b-col class="translated-container mb-3" lg="6" md="6" sm="12">
          <b-form-textarea
            id="translation-result"
            class="w-100 textarea-container"
            rows="9"
            v-if="wordTranslated"
            :value="wordTranslated"
          >
          </b-form-textarea>

          <b-form-textarea
            class="w-100"
            rows="9"
            placeholder="The translation results will show here!"
            aria-label="Text already translated"
            v-else
          ></b-form-textarea>
        </b-col>
      </b-row>
    </div>
  </b-container>
</template>

<script>
import axios from "axios";
import DelButton from "./DelButton";
import LangSelector from "./LangSelector";
import SwitcherTranslation from "./Switcher";
import DarckMod from "./DarckMod";

export default {
  name: "TranslationPage",
  components: {
    DelButton,
    LangSelector,
    SwitcherTranslation,
    DarckMod
  },
  data() {
    return {
      placeholder: "Type something ...",
      wordTranslated: "",
      inputValue: "",
      languageFrom: null,
      languageTo: null,
      languageTitle: null,
      loading: true
    };
  },
  mounted() {
    this.preloaderSpinner();
  },
  methods: {
    preloaderSpinner() {
      setTimeout(() => {
        this.loading = false;
      }, 1500);
    },
    translate(e) {
      if (e.key == "Enter") {
        axios
          .get(
            `${
              this.languageFrom
            }-${
              this.languageTo
            }${
              this.inputValue
            }`
          )
          .then(response => {
            this.wordTranslated = response.data.text[0];
          });
      }
    },
    updatePairFrom(index) {
      this.languageFrom = index.value;
    },
    updatePairTo(index) {
      this.languageTitle = index.text + " Female";
      this.languageTo = index.value;
    },
    deleteTextValue() {
      this.inputValue = "";
      this.wordTranslated = "";
    }
  }
};
</script>
