<template>
  <div>
    <h1 class="text-7xl font-black text-center">New on the blog</h1>
    <ul class="grid grid-cols-3 gap-8 mt-8">
      <PostPreview v-for="post in posts" :key="post.slug" :post="post"></PostPreview>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const posts = await $content()
      .only(['title', 'image', 'tags', 'slug'])
      .sortBy('createdAt', 'desc')
      .fetch()
      
    console.log("posts", posts)  

    return {
      posts,
    }
  },
}
</script>
