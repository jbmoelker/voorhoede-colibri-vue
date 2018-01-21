<template>
  <figure class="image-figure">
    <FixedRatio v-if="isResponsiveImage" :width="image.width" :height="image.height">
      <picture>
        <!--[if IE 9]><video style="display:none"><![endif]-->
        <source media="(min-width: 570px)" type="image/webp" :srcset="imageUrl(image.src, { fm: 'webp', width: 990 })">
        <source media="(min-width: 320px)" type="image/webp" :srcset="imageUrl(image.src, { fm: 'webp', width: 570 })">
        <source media="(min-width: 570px)" :srcset="imageUrl(image.src, { width: 990 })">
        <source media="(min-width: 320px)" :srcset="imageUrl(image.src, { width: 570 })">
        <!--[if IE 9]><![endif]-->
        <img class="image-figure__image" :alt="image.alt" :src="imageUrl(image.src, { width: 320 })">
      </picture>
    </FixedRatio>
    <img v-if="!isResponsiveImage" class="image-figure__image" :alt="image.alt" :src="image.src">
    <figcaption v-if="image.title" class="image-figure__caption">{{ image.title }}</figcaption>
  </figure>
</template>

<style>
  .image-figure {
    margin: 0;
  }

  .image-figure__image {
    width: 100%;
  }

  .image-figure__caption {
    text-align: center;
  }
</style>

<script>
  import FixedRatio from './FixedRatio'
  import imageUrl from '../lib/image-url'

  export default {
    components: { FixedRatio },
    props: {
      image: { type: Object, required: true },
    },
    computed: {
      isResponsiveImage: function () { return this.image.width && this.image.height }
    },
    methods: { imageUrl },
  }
</script>

