<template>
  <div id="app">
    <fw-preview ref="preview"></fw-preview>
    <fw-lista :elements="elements"></fw-lista>
  </div>
</template>

<script>
import Lista from '/components/Lista';
import Preview from '/components/Preview';
import elements from '/assets/frameworks.json';
import { EventBus } from '/event-bus.js';

export default {
  name: 'App',
  components: {
    'fw-lista': Lista,
    'fw-preview': Preview
  },
  data() {
    return {
      elements
    }
  },
  mounted() {
    EventBus.$on('click-element', data => {
      this.$refs.preview.setElement(data);
    });
  }
}
</script>

<style lang="postcss">
  :root {
    --bgcolor: #ddd;
    --textcolor: #fff;

    background: linear-gradient(140deg, #495e54 30%, #35495d 40%, #4fc08c 80%);
    height: 100vh;
  }

  #app {
    max-width: 900px;
    margin: 4em auto;
    display: flex;
    justify-content: center;
  }

  @media screen and (max-width: 850px) {
    #app {
      flex-direction: column;
      align-items: center;
    }
  }
</style>
