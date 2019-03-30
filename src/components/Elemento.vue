<template>
  <div class="elemento" @click="show(numid)" @mouseenter="play(blip)">
    {{ element.name }}
  </div>
</template>

<script>
import { EventBus } from '/event-bus.js';
import blip from '/assets/blip.mp3';
import click from '/assets/click.mp3';
export default {
  name: 'FwElemento',
  props: {
    element: {
      type: Object,
      default: () => ({})
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
  mounted() {
    this.blip.volume = 0.2;
    this.preloadImage(this.element.image);
    this.$el.style.setProperty('--bgcolor', this.element.bgcolor);
    if (this.element.textcolor)
      this.$el.style.setProperty('--textcolor', this.element.textcolor);
  },
  methods: {
    play(sound) {
      sound.currentTime = 0;
      sound.play();
    },
    preloadImage(image) {
      document.head.innerHTML += `<link rel="prefetch" href="${image}">`;
    },
    show(id) {
      EventBus.$emit('click-element', this.element);
      this.play(this.click);
    }
  }
}
</script>

<style lang="postcss">
  .elemento {
    display: flex;
    justify-content: center;
    align-items: center;
    background: #222;
    border: 1px solid #fff;
    width: 100px;
    height: 100px;
    color: #ddd;
    font-family: Arial, sans-serif;
    box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.5);
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
