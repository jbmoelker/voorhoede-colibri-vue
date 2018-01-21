<template>
  <div class="page-content">

    <template v-if="content" v-html="content" />
    <template v-if="items" v-for="(item, index) in items">
      <template v-if="item.type === 'html'">
        <div v-html="item.html" :key="index"></div>
      </template>
      <template v-if="item.type === 'image'">
        <image-figure :image="item" :key="index" />
      </template>
    </template>
  </div>
</template>

<style>
  .page-content {
    max-width: 56em;
    padding: 2em;
    margin: 0 auto;
  }

  .page-content h2 {
    font-size: 1.4em;
    font-weight: 500;
  }

  .page-content p:empty {
    display: none;
  }

  .page-content pre {
    background-color: #f9f9f9;
    box-shadow: inset 1px 1px 5px rgba(0,0,0,0.05);
    padding: 0.5em;
    border-radius: 2px;
    overflow-x: auto;
  }

  .page-content pre code {
    background-color: transparent;
    padding: 0;
  }

  .page-content ul {
    line-height: 1.5;
  }

  .page-content li {
    margin: 0 0 0.5em 0;
  }
</style>

<script>
  import ImageFigure from './ImageFigure'

  export default {
    components: { ImageFigure },
    props: {
      content: { type: String },
      items: { type: Array },
    }
  }
</script>

