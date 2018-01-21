<template>
  <nav class="page-nav">
    <details>
      <summary>
        <h2>{{ title }}</h2>
      </summary>
      <ol class="page-nav__list">
        <li v-for="item in items" :key="item.id">
          <a :href="`#${item.id}`" v-html="item.html"></a>
        </li>
      </ol>
    </details>
  </nav>
</template>

<style>
  .page-nav__list {
    list-style: none;
  }
</style>

<script>
  export default {
    props: {
      items: { type: Array, required: true },
      title: { type: String, default: 'Table of Contents' },
    }
  }
</script>
