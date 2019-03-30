<template>
  <div class="preview">
    <h2>{{ element.name }}</h2>
    <img v-show="element.image" :src="element.image" :alt="element.name">
    <a :href="element.url">{{ element.url }}</a>
  </div>
</template>

<script>
export default {
  name: 'FwPreview',
  data() {
    return {
      element: {
        name: '',
        image: '',
        url: ''
      }
    }
  },
  methods: {
    setElement(e) {
      this.element = e;
    }
  }
}
</script>

<style lang="postcss" scoped>
  .preview {
    border: 3px solid #fff;
    background: #222;
    min-width: 300px;
    height: 300px;
    display: flex;
    flex-direction: column;
    align-items: center;
    box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.5);
    justify-content: center;

    & h2 {
      color: #fff;
      font-family: Montserrat, sans-serif;
      font-weight: 700;
      font-size: 42px;
      letter-spacing: -2px;
      text-align: center;
      margin: 0 0 0.6em 0;
    }

    & img {
      max-width: 100px;
      margin-bottom: 25px;
    }

    & a {
      font-family: Montserrat, sans-serif;
      font-size: 16px;
      color: #888;
    }
  }
</style>
