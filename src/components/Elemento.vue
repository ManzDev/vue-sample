<template>
  <div
    class="elemento"
    @click="show(numid)"
    @mouseenter="soundOver()"
  >
    {{ element.name }}
  </div>
</template>

<script>
import blip from '/assets/blip.mp3';
import click from '/assets/click.mp3';
export default {
  name: 'FwElemento',
  props: {
    element: {
      type: Object,
      default: () => {}
    },
    numid: {
      type: Number,
      default: 0
    }
  },
  data() {
    return {
      blip: new Audio(blip),
      click: new Audio(click)
    }
  },
  computed: {
    preview() { return this.$parent.$parent.$refs.preview }
    // preview() { return this.$root.$children[0].$refs.preview }
  },
  mounted() {
    document.head.innerHTML += `<link rel="prefetch" href="${this.element.image}">`;
    this.$el.style.setProperty('--bgcolor', this.element.bgcolor);
    if (this.element.textcolor)
      this.$el.style.setProperty('--textcolor', this.element.textcolor);
  },
  methods: {
    show(id) {
      this.preview.setElement(this.element);
      this.click.currentTime = 0;
      this.click.play();
    },
    soundOver() {
      this.blip.currentTime = 0;
      this.blip.play();
    }
  }
}
</script>

<style lang="postcss">
  .elemento {
    display: flex;
    justify-content: center;
    align-items: center;
    border: 1px solid #fff;
    width: 100px;
    height: 100px;
    color: #ddd;
    font-family: Arial, sans-serif;
    transition:
      background 1s ease,
      color 0.2s ease-in-out;

    &:hover {
      background: var(--bgcolor);
      color: var(--textcolor);
      cursor: pointer;
    }
  }
</style>
