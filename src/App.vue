<template>
  <div
    class="container flex flex-col gap-5 m-auto mt-5 p-5 border border-teal-400 border-solid rounded font-body"
  >
    <h1 class="text-center text-4xl font-semibold">Table</h1>
    <post-form @createPost="createPost" />
    <post-list
      :posts="myJson"
      @deletePost="deletePost"
      @editName="editName"
      @editDescription="editDescription"
    />
    <post-delete
      v-if="myJson.length !== 0"
      class="self-end"
      @deletePosts="deletePosts"
    />
  </div>
</template>

<script>
import PostList from "./components/PostList.vue";
import PostForm from "./components/PostForm.vue";
import PostDelete from "./components/actions/PostsDelete.vue";

import json from "./json/PostData.json";
export default {
  data() {
    return {
      myJson: json,
    };
  },
  components: {
    PostList,
    PostForm,
    PostDelete,
  },
  methods: {
    createPost(newPost) {
      newPost.id = this.myJson.length + 1;
      this.myJson.push(newPost);
    },
    deletePosts() {
      this.myJson.shift();
    },
    deletePost(index) {
      this.myJson.splice(index, 1);
      for (let i = index; i < this.myJson.length; i++) {
        this.myJson[i].id--;
      }
    },
    editName(post) {
      this.myJson[post.id].title = post.title;
    },
    editDescription(post) {
      console.log(post.body);
      this.myJson[post.id].body = post.body;
    },
  },
};
</script>

<style></style>
