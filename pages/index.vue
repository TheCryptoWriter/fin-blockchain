<template>
  <main>
    <section class="container">
      <div class="container__content">
      </div>
    </section>
  </main>
</template>

<script>
import { createClient } from '../plugins/contentful';

const contentfulClient = createClient();

export default {
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