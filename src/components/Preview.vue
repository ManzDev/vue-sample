<template>
  <div class="preview">
    <h2>{{ name }}</h2>
    <img
      v-show="image"
      :src="image"
      :alt="name"
    >
    <a href="url">{{ url }}</a>
  </div>
</template>

<script>
export default {
  name: 'FwPreview',
  data() {
    return {
      name: '',
      image: '',
      url: ''
    }
  },
  methods: {
    setElement(e) {
      this.name = e.name;
      this.image = e.image;
      this.url = e.url;
    }
  }
}
</script>

<style lang="postcss" scoped>
  .preview {
    border: 3px solid #fff;
    width: 300px;
    height: 300px;
    display: flex;
    flex-direction: column;
    align-items: center;
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
