<template>
  <div id="app">
    <h1>String Utilities</h1>
    <section>
      <div class="form-group">
        <textarea
          v-model="input"
          class="form-control"
          rows="10"
          @input="updateOutput"
        />
      </div>
      <div class="form-group">
        <select
          v-model="selectedFunction"
          class="form-control"
          @change="updateOutput"
        >
          <option
            v-for="[name] in Object.entries(functions)"
            :key="name"
            :value="name"
          >
            {{ name }}
          </option>
        </select>
      </div>
      <div class="form-group">
        <div class="custom-control custom-switch">
          <input
            id="splitOnNewLineSwitch"
            v-model="splitOnNewLine"
            type="checkbox"
            class="custom-control-input"
            :disabled="splitOnNewLineSwitchIsDisabled"
            @change="updateOutput"
          />
          <label class="custom-control-label" for="splitOnNewLineSwitch">
            Split on New Line
          </label>
        </div>
      </div>
      <div class="form-group">
        <textarea
          v-model="output"
          v-clipboard:copy="output"
          class="form-control"
          rows="10"
        />
      </div>
      <div class="form-group">
        <button v-clipboard:copy="output" class="btn btn-primary">
          Copy to Clipboard
        </button>
      </div>
    </section>
  </div>
</template>

<script>
import {
  camelCase,
  capitalize,
  deburr,
  escape,
  escapeRegExp,
  kebabCase,
  lowerCase,
  lowerFirst,
  snakeCase,
  startCase,
  toLower,
  toUpper,
  trim,
  trimEnd,
  trimStart,
  unescape,
  upperCase,
  upperFirst,
  words,
} from 'lodash';

import { parse, stringify } from 'csv/lib/sync';

const alwaysSplitOnNewLineFunctions = new Set([
  'CSV to JSON Array',
  'JSON Array to CSV',
]);

function csvToJsonArray(input) {
  try {
    return JSON.stringify(parse(input, { columns: true }), null, 2);
  } catch (err) {
    return err;
  }
}

function jsonArrayToCsv(input) {
  try {
    const obj = JSON.parse(input);
    return stringify(obj, { header: true });
  } catch (err) {
    return err;
  }
}

export default {
  name: 'App',
  components: {},
  data() {
    return {
      input: '',
      functions: {
        'Base64 Decode': btoa,
        'Base64 Encode': atob,
        'Camel Case': camelCase,
        Capitalize: capitalize,
        'CSV to JSON Array': csvToJsonArray,
        Deburr: deburr,
        'HTML Escape (Simple)': escape,
        'HTML Unescape (Simple)': unescape,
        'JSON Array to CSV': jsonArrayToCsv,
        'Kebab Case': kebabCase,
        'Lower Case (Words)': lowerCase,
        'Lower Case (String': toLower,
        'Lower First': lowerFirst,
        'Regex Escape': escapeRegExp,
        'Snake Case': snakeCase,
        'Start Case': startCase,
        Trim: trim,
        'Trim End': trimEnd,
        'Trim Start': trimStart,
        'Upper Case (String)': toUpper,
        'Upper Case (Words)': upperCase,
        'Upper First': upperFirst,
        'URI Decode': decodeURI,
        'URI Decode Component': decodeURIComponent,
        'URI Encode': encodeURI,
        'URI Encode Component': encodeURIComponent,
        Words: words,
      },
      selectedFunction: 'Base64 Decode',
      splitOnNewLine: true,
      splitOnNewLineSwitchIsDisabled: false,
      output: '',
    };
  },
  methods: {
    updateOutput() {
      const f = this.functions[this.selectedFunction];

      if (alwaysSplitOnNewLineFunctions.has(this.selectedFunction)) {
        this.splitOnNewLine = false;
        this.splitOnNewLineSwitchIsDisabled = true;
      } else {
        this.splitOnNewLineSwitchIsDisabled = false;
      }

      try {
        this.output = this.splitOnNewLine
          ? this.input
              .split(/\r\n|\r|\n/)
              .map(f)
              .join('\n')
          : f(this.input);
      } catch (err) {
        this.output = err;
      }
    },
  },
};
</script>

<style>
#app {
  text-align: center;
}
</style>
