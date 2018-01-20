<template>
  <main>
    <home-header :title="page.headerTitle" :subtitle="page.subtitle" />
    <section>
      USPs
    </section>
  </main>
</template>

<script>
import HomeHeader from '~/components/HomeHeader.vue'

export default {
  components: { HomeHeader },
  data () {
    return {
      page: {
        headerTitle: 'We are <strong>De Voorhoede</strong>',
        subtitle: 'Makers of websites and web apps<br>for everyone'
      }
    }
  }
}
</script>

<style>
</style>
