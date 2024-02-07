<template>
  <div class="flex flex-col gap-3">
    <h1 class="font-semibold">Create</h1>
    <post-create @createPost="createPost" />
  </div>
</template>

<script>
import PostCreate from "./PostCreate.vue";
export default {
  components: {
    PostCreate,
  },
  methods: {
    createPost(newPost) {
      this.$emit("createPost", newPost);
    },
  },
};
</script>

<style></style>
