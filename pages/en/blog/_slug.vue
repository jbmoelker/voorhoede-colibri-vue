<template>
  <article>

    <h1>{{ item.title }}</h1>
    <p>{{ item.teaser }}</p>

    <PageNav :items="item.navItems" />

    <div>
      <BlogAuthors :authors="item.authors" />
      <!--<time datetime="{{ item.publishDate }}">{{ prettyDate(item.publishDate) }}</time>-->
    </div>

    <PageContent :items="item.bodyItems" />

  </article>
</template>

<script>
  import api from '~/api/client'
  import { BlogAuthors, PageContent, PageNav } from '~/components/'

  export default {
    components: { BlogAuthors, PageContent, PageNav },

    async asyncData ({ params }) {
      const { slug } = params
      const fields = ['title', 'social', 'teaser', 'navItems', 'authors', 'publishDate', 'bodyItems']
      const item = await api.getItem({ collection: 'posts', slug, fields })
      return { item, slug }
    }
  }
</script>
