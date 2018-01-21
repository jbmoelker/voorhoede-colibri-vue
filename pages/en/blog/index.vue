<template>
  <main>
    <h1>{{ page.title }}</h1>
    <p>{{ page.subtitle }}</p>
      <article v-for="item in items" :key="item.slug">
        {{ item.publishDate }}
        <a :href="`/en/blog/${item.slug}`">
          {{ item.title }}
        </a>
        <blog-authors :authors="item.authors" />
      </article>
  </main>
</template>

<script>
  import api from '~/api/client'
  import BlogAuthors from '~/components/BlogAuthors'

  export default {
    components: { BlogAuthors },

    async asyncData () {
      const [ page, items ] = await Promise.all([
        api.getPage({ name: 'blog' }),
        api.getItems({ collection: 'posts', fields: ['authors', 'publishDate', 'slug', 'title'] }),
      ])
      return { page, items }
    }
  }
</script>
