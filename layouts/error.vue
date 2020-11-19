<template>
  <v-app>
    <h1 v-if="error.statusCode === 404">
      <v-icon>mdi-information</v-icon>{{ pageNotFound }}
    </h1>
    <h1 v-else><v-icon>mdi-information</v-icon>{{ otherError }}</h1>
    <NuxtLink to="/"> Home page </NuxtLink>
  </v-app>
</template>

<script>
export default {
  layout: 'empty',
  props: {
    error: {
      type: Object,
      default: null,
    },
  },
  data() {
    return {
      pageNotFound: '404 Not Found',
      otherError: 'An error occurred',
    }
  },
  head() {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError
    return {
      title,
    }
  },
}
</script>
