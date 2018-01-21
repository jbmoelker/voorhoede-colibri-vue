<template>
  <span>
    <Avatar v-for="author in authors" :key="author.name" :src="author.image.url" />
    by {{ authors.map(author => author.name).join(' & ') }}
  </span>
</template>

<script>
  import Avatar from './Avatar'

  export default {
    components: { Avatar },
    props: {
      authors: { type: Array, required: true }
    }
  }
</script>
