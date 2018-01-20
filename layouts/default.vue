<template>
  <div>
    <app-header />
    <nuxt/>
    <app-footer />
  </div>
</template>

<script>
  import AppFooter from '~/components/AppFooter'
  import AppHeader from '~/components/AppHeader'

  export default {
    components: { AppFooter, AppHeader }
  }
</script>
