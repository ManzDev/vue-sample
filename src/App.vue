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

    background: linear-gradient(140deg, #495e54 30%, #35495d 40%, #4fc08c 80%);
    height: 100vh;
  }

  #app {
    margin-top: 4em;
    display: flex;
    justify-content: center;
  }

  @media screen and (max-width: 800px) {
    #app {
      flex-direction: column;
      align-items: center;
    }
  }
</style>
