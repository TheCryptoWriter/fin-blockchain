<template>
  <section class="container">
    <Navigation />
    <div class="container__content">
      <h1>Please select a page you wish to view</h1>
      <p>This is a website for demo purposes of using Nuxt & Contentful together</p>
    </div>
  </section>
</template>

<script>
import Navigation from '../components/global/Navigation';
import { createClient } from '../plugins/contentful';

const contentfulClient = createClient();

export default {
  components: {
    Navigation
  },
  asyncData({ env }) {
    return Promise.all([
      // fetch all blog posts sorted by creation date
      contentfulClient.getEntries({
        'content_type': 'page',
        order: '-sys.createdAt'
      })
    ]).then(([pages]) => {
      // return data that should be available
      // in the template
      return {
        collections: pages.items
      }
    }).catch(console.error)
  }
}
</script>