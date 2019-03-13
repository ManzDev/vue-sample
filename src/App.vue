<template>
  <div id="app">
    <fw-preview ref="preview"></fw-preview>
    <fw-lista></fw-lista>
  </div>
</template>

<script>
import Lista from '/components/Lista';
import Preview from '/components/Preview';
import elements from '/assets/frameworks.json';
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
  }
}
</script>

<style lang="postcss">
  :root {
    --bgcolor: #ddd;
    --textcolor: #fff;

    background: #222;
  }

  #app {
    margin-top: 4em;
    display: flex;
    justify-content: center;
  }
</style>
