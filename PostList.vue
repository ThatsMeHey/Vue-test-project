<template>
  <div v-if="posts.length > 0">
    <h3>List of users</h3>
    <post-item
        v-for="post in posts"
        :post = "post"
        :key="post.id"
        @remove="$emit('remove', post)"
    />
  </div>
  <h2 v-else style="color: red">
    List of posts is empty
  </h2>
</template>

<script>
import PostItem from "@/components/PostItem.vue";

export default {
  components: {PostItem},
  props: {
    posts: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
.post
{
  padding: 15px;
  border: 3px solid salmon;
  margin: 15px;
}
</style>