<template>
  <form @submit.prevent>
    <h4>Creating post</h4>
    <my-input
        v-model="post.title"
        type="text"
        placeholder="Name"
    />
    <my-input
        v-model="post.body"
        type="text"
        placeholder="Description"
    />
    <my-button
      class="btn"
      style="align-self: flex-end; margin-right: 15px"
      @click="createPost"
      >
      Create
    </my-button>
  </form>
</template>

<script>
import MyButton from "@/components/UI/MyButton.vue";
import MyInput from "@/components/UI/MyInput.vue";

export default {
  components: {MyInput, MyButton},
  data() {
    return {
      post: {
        title: '',
        body: ''
      }
    }
  },
  methods: {
    createPost() {
      this.post.id = Date.now()
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: ''
      }
    }
  }
}
</script>

<style scoped>
form{
  display: flex;
  flex-direction: column;
}


</style>