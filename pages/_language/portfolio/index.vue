<template>
  <main>
    <h1>{{ page.title }}</h1>
    <p>{{ page.subtitle }}</p>
    <a v-for="item in items" :key="item.slug" :href="`/${language}/portfolio/${item.slug}`">
      <div>
        <h2>{{ item.title }}</h2>
        <p>{{ item.subtitle }}</p>
      </div>
    </a>
  </main>
</template>

<script>
  import api from '~/api/client'

  export default {
    async asyncData ({ params }) {
      const { language } = params
      const [ page, items ] = await Promise.all([
        api.getPage({ name: 'portfolio', language }),
        api.getItems({ collection: 'projects', language, fields: ['slug', 'title', 'subtitle'] }),
      ])
      return { language, page, items }
    }
  }
</script>
