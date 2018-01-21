<template>
  <article>

    <h1>{{ item.title }}</h1>
    <p>{{ item.subtitle }}</p>

    <PageContent :items="item.bodyItems" />

  </article>
</template>

<script>
  import { PageContent } from '~/components'
  import api from '~/api/client'

  export default {
    components: { PageContent },

    async asyncData ({ params }) {
      const { language, slug } = params
      const fields = ['title', 'social', 'subtitle', 'bodyItems']
      const item = await api.getItem({ collection: 'projects', slug, language, fields })
      return { item, language }
    }
  }
</script>
