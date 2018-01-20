<template>
  <div class="fixed-ratio" :style="{ paddingBottom: `${ratio}%` }">
    <div class="fixed-ratio__content">
      <slot></slot>
    </div>
  </div>
</template>

<style>
  /**
   * Force content inside an element to have a fixed ratio. This technique prevents reflow when loading images.
   * Read all about it: https://www.voorhoede.nl/en/blog/say-no-to-image-reflow/
   */
  .fixed-ratio {
    display: block;
    position: relative;
    height: 0;
    overflow: hidden;
  }

  .fixed-ratio__content {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    max-width: inherit;
  }

  .fixed-ratio__content > * {
    width: 100%;
    height: 100%;
  }
</style>

<script>
  export default {
    props: ['width', 'height'],
    computed: {
      ratio: function() { return this.height/this.width * 100 }
    }
  }
</script>
