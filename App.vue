<template>
  <div class="app">
    <h1>Page with posts</h1>
    <input type="text" v-model.trim="modificatorValue">
    <my-button
      @click="showDialog"
      style="margin: 15px 0;"
      >
      Create post
    </my-button>
    <my-dialog v-model:show="displayVisible">
      <post-form
        @create="createPost"
      />
    </my-dialog>
    <post-list
        :posts="posts"
        @remove="removePost"
    />
  </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyDialog from "@/components/UI/MyDialog.vue";
import MyButton from "@/components/UI/MyButton.vue";

export default {
  components: {
    MyButton,
    MyDialog,
    PostList,
    PostForm
  },
  data() {
    return {
      posts: [
        {id: 1, title: 'Slay', body: 'Slay me queen 🥺😑🥰'},
        {id: 2, title: 'Yass', body: 'I com 🥰'},
        {id: 3, title: 'Ass', body: 'Ew, stinks'},
        {id: 4, title: 'Jiafei', body: 'Queen, yay'},
      ],
      displayVisible: false,
      modificatorValue: ''
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.displayVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id);
    },
    showDialog() {
      this.displayVisible = true;
    },
  }
}
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  }

.app
{
  padding: 20px;
}
</style>
