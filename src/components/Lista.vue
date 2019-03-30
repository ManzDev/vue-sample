<template>
  <div class="lista">
    <fw-elemento
      v-for="(e,i) in elements"
      :key="i"
      :numid="i"
      :element="e"
    ></fw-elemento>
  </div>
</template>

<script>
import Elemento from '/components/Elemento';
export default {
  name: 'FwLista',
  components: {
    'fw-elemento': Elemento
  },
  props: {
    elements: {
      type: Array,
      default: () => ({}),
      required: true
    }
  }
}
</script>

<style lang="postcss">
  .lista {
    display: flex;
    flex-wrap: wrap;
    margin: auto 0;
    max-width: 525px;
  }
</style>
