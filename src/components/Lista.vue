<template>
  <div class="lista">
    <fw-elemento
      v-for="(e,i) in elements"
      :key="i"
      :numid="i"
      :element="elements[i]"
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
  data() {
    return {
      elements: this.$parent.elements
    }
  }
}
</script>

<style lang="postcss">
  .lista {
    display: flex;
    flex-wrap: wrap;
    align-content: flex-start;
    width: 600px;
  }
</style>
