<template>
  <div class="posts">
    <main>
      <h2>Posts</h2>
      <div
        v-for="post in posts"
        :key="post.id"
        class="post"
      >
        <h3>
          <a :href="`blog/${post.slug}`">{{ post.title.rendered }}</a>
        </h3>
        <div v-html="post.excerpt.rendered" />
        <a
          :href="`blog/${post.slug}`"
          class="readmore"
        >
          Read more ⟶
        </a>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  computed: {
    posts () {
      return this.$store.state.posts
    }
  },
  created () {
    this.$store.dispatch('getPosts')
  }
}
</script>
