<template>
  <header class="home-header">

    <fixed-ratio :width="720" :height="310">
      <object
        role="presentation"
        type="image/svg+xml"
        data="/voorhoede-animation.svg"
        class="home-header__image"
        :class="{ 'home-header__image--loaded': imageLoaded }"
        v-on:load="setImageLoaded"
      ></object>
    </fixed-ratio>

    <h1 v-html="title"></h1>
    <div v-html="subtitle"></div>

    <arrow-down />
  </header>
</template>

<style>
  @import '~assets/variables.css';

  .home-header {
    position: relative;
    padding: 0 20px 80px;
    background-color: var(--brand-yellow);
    color: var(--brand-blue);
    text-align: center;
  }

  .home-header__image {
    opacity: 0;
    transition: opacity .5s ease;
  }

  .home-header__image--loaded {
    opacity: 1;
  }
</style>

<script>
  import ArrowDown from './ArrowDown'
  import FixedRatio from './FixedRatio'

  export default {
    components: { ArrowDown, FixedRatio },
    props: ['title', 'subtitle'],

    data () {
      return {
        imageLoaded: false,
      }
    },

    methods: {
      setImageLoaded: function () {
        this.imageLoaded = true
      }
    }
  }
</script>
